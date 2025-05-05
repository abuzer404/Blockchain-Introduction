# Vote Storage 

// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

contract Contract {
    enum Choices { Yes, No }

    struct Vote {
        Choices choice;
        address voter;
    }

    Vote public lastVote;

    function createVote(Choices choice) external {
        lastVote = Vote({
            choice: choice,
            voter: msg.sender
        });
    }

    function vote() public view returns (Choices, address) {
        return (lastVote.choice, lastVote.voter);
    }
}

# Vote Memory

// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

contract Contract {
    enum Choices { Yes, No }

    struct Vote {
        Choices choice;
        address voter;
    }

    function createVote(Choices choice) external view returns (Vote memory) {
        return Vote({
            choice: choice,
            voter: msg.sender
        });
    }
}


# vote array

// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

contract Contract {
    enum Choices { Yes, No }

    struct Vote {
        Choices choice;
        address voter;
    }

    Vote[] public votes;

    function createVote(Choices choice) external {
        votes.push(Vote({
            choice: choice,
            voter: msg.sender
        }));
    }
}

# Choice Lookup

// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

contract Contract {
    enum Choices { Yes, No }

    struct Vote {
        Choices choice;
        address voter;
    }

    Vote[] public votes;
    mapping(address => bool) public hasVoted;
    mapping(address => Choices) private choices;

    function createVote(Choices choice) external {
        require(!hasVoted[msg.sender], "Already voted");

        votes.push(Vote({
            choice: choice,
            voter: msg.sender
        }));

        hasVoted[msg.sender] = true;
        choices[msg.sender] = choice;
    }

    function findChoice(address voter) external view returns (Choices) {
        require(hasVoted[voter], "Voter has not voted");
        return choices[voter];
    }
}

# single vote

// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

contract Contract {
    enum Choices { Yes, No }

    struct Vote {
        Choices choice;
        address voter;
    }

    Vote[] public votes;
    mapping(address => bool) public hasVoted;
    mapping(address => Choices) private choices;
    mapping(address => uint256) private voteIndex;

    function createVote(Choices choice) external {
        require(!hasVoted[msg.sender], "Already voted");

        votes.push(Vote({
            choice: choice,
            voter: msg.sender
        }));

        hasVoted[msg.sender] = true;
        choices[msg.sender] = choice;
        voteIndex[msg.sender] = votes.length - 1;
    }

    function findChoice(address voter) external view returns (Choices) {
        require(hasVoted[voter], "Voter has not voted");
        return choices[voter];
    }

    function changeVote(Choices newChoice) external {
        require(hasVoted[msg.sender], "No vote to change");

        // update mappings
        choices[msg.sender] = newChoice;

        // update the vote in the array
        uint256 index = voteIndex[msg.sender];
        votes[index].choice = newChoice;
    }
}

# change vote

// SPDX-License-Identifier: MIT
pragma solidity 0.8.20;

contract Contract {
    enum Choices { Yes, No }

    struct Vote {
        Choices choice;
        address voter;
    }

    Vote[] public votes;
    mapping(address => bool) public hasVoted;
    mapping(address => Choices) private choices;
    mapping(address => uint256) private voteIndex;

    function createVote(Choices choice) external {
        require(!hasVoted[msg.sender], "Already voted");

        votes.push(Vote({
            choice: choice,
            voter: msg.sender
        }));

        hasVoted[msg.sender] = true;
        choices[msg.sender] = choice;
        voteIndex[msg.sender] = votes.length - 1;
    }

    function findChoice(address voter) external view returns (Choices) {
        require(hasVoted[voter], "Voter has not voted");
        return choices[voter];
    }

    function changeVote(Choices newChoice) external {
        require(hasVoted[msg.sender], "No vote to change");

        // update mappings
        choices[msg.sender] = newChoice;

        // update the vote in the array
        uint256 index = voteIndex[msg.sender];
        votes[index].choice = newChoice;
    }
}
