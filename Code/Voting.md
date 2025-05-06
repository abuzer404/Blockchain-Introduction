// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract Voting {
    struct Proposal {
        address target;
        bytes data;
        uint yesCount;
        uint noCount;
        bool executed;
    }
     
    Proposal[] public proposals;
    mapping(uint => mapping(address => bool)) public hasVoted;
    mapping(uint => mapping(address => bool)) public voteDirection;
    mapping(address => bool) public members;
    
    event ProposalCreated(uint proposalId);
    event VoteCast(uint proposalId, address voter);
    event ProposalExecuted(uint proposalId, bool success);

    constructor(address[] memory _members) {
        members[msg.sender] = true; 
        for (uint i = 0; i < _members.length; i++) {
            members[_members[i]] = true;
        }
    }

     // Creating a Proposal
    function newProposal(address _target, bytes calldata _data) external {
        require(members[msg.sender], "Only members can create proposals");
        Proposal memory newProposal = Proposal({
            target: _target,
            data: _data,
            yesCount: 0,
            noCount: 0,
            executed: false
        });
        proposals.push(newProposal);
        emit ProposalCreated(proposals.length - 1);
    }
    
    // Voting a proposal of proposalId
    function castVote(uint proposalId, bool support) external {
        require(members[msg.sender], "Only members can vote");
        require(proposalId < proposals.length, "Proposal does not exist");
        require(!proposals[proposalId].executed, "Proposal already executed");

        // If the voter has already voted, adjust the counts based on their previous vote
        if (hasVoted[proposalId][msg.sender]) {
            if (voteDirection[proposalId][msg.sender]) {
                proposals[proposalId].yesCount--;
            } else {
                proposals[proposalId].noCount--;
                }
        } else {
             // Mark that the voter has now voted
            hasVoted[proposalId][msg.sender] = true;
        }

        // Update the vote counts based on the new vote
        if (support) {
            proposals[proposalId].yesCount++;
        } else {
            proposals[proposalId].noCount++;
        }

        // Record the current vote direction
        voteDirection[proposalId][msg.sender] = support;
        emit VoteCast(proposalId, msg.sender);

        if (proposals[proposalId].yesCount >= 10 && !proposals[proposalId].executed) {
            (bool success, ) = proposals[proposalId].target.call(proposals[proposalId].data);
            proposals[proposalId].executed = true;
            emit ProposalExecuted(proposalId, success);
        }
    }
}