# Bitcoin Community DAO Smart Contract

This smart contract implements a **Decentralized Autonomous Organization (DAO)** for managing community projects, handling proposals, voting, and fund allocation. It enables members to propose initiatives, vote on them, and manage the DAO's treasury for local development purposes.

---

## Key Features

### 1. **Proposal Management**
- Submit proposals with a title, description, and funding amount.
- Proposals have a defined voting period and status (active, done, or void).
- Cancel proposals before the voting period ends if necessary.

### 2. **Voting System**
- DAO members can vote for or against proposals.
- Votes are recorded and cannot be changed or duplicated.
- Delegate voting rights to another DAO member.

### 3. **Fund Management**
- DAO treasury holds funds collected from members or external sources.
- Approved proposals can withdraw the required amount from the treasury.
- Members can withdraw their stake or transfer reputation.

### 4. **Membership Management**
- Members join the DAO by staking a minimum amount.
- Members earn reputation points for participation.
- Transfer reputation points to another member.

### 5. **Reputation System**
- Reputation tracks member contributions and activity in the DAO.
- Increased reputation signifies higher trust and contributions.

---

## Data Structures

### **Maps**
1. **`proposals`**
   - Tracks all proposals submitted to the DAO.
   - Fields include title, description, proposer, funding amount, voting counts, and status.

2. **`votes`**
   - Records each member’s voting activity for specific proposals.

3. **`member-details`**
   - Maintains membership and reputation data for DAO members.

### **Variables**
- **`proposal-count`**: Tracks the total number of proposals submitted.
- **`dao-treasury`**: Holds the DAO's current treasury balance.

---

## Functions

### **Public Functions**

#### 1. Proposal Management
- **`submit-proposal`**: Submit a new proposal for DAO consideration.
- **`execute-proposal`**: Disburse funds to an approved proposal’s proposer.
- **`cancel-proposal`**: Cancel a proposal before the voting period ends.

#### 2. Voting
- **`cast-vote`**: Vote for or against a proposal during the active period.
- **`delegate-vote`**: Delegate voting rights for a specific proposal to another member.

#### 3. Membership
- **`join-dao`**: Join the DAO by staking funds and earning initial reputation.
- **`increase-reputation`**: Increase the reputation of a specific member.
- **`transfer-reputation`**: Transfer reputation points to another member.
- **`withdraw-stake`**: Withdraw previously staked funds.

#### 4. Fund Management
- **`fund-dao`**: Add funds to the DAO treasury.
- **`get-treasury-balance`**: Check the DAO's current treasury balance.

---

### **Read-Only Functions**
- **`get-proposal`**: Retrieve details of a specific proposal.
- **`get-member-reputation`**: Check a member’s reputation score.
- **`get-treasury-balance`**: View the DAO’s current treasury funds.

---

## Constants
- **`VOTING_PERIOD`**: ~10 days in blocks (1440 blocks).
- **`MIN_PROPOSAL_AMOUNT`**: Minimum funding amount for a proposal (1,000,000 microSTX).
- **`REQUIRED_APPROVAL_PERCENTAGE`**: Minimum 70% approval votes required for a proposal to pass.

---

## Errors
- **`ERR-NOT-AUTHORIZED (u100)`**: Action is restricted to DAO members or specific roles.
- **`ERR-INVALID-PROPOSAL (u101)`**: Proposal details do not meet the requirements.
- **`ERR-ALREADY-VOTED (u102)`**: Member has already voted on this proposal.
- **`ERR-PROPOSAL-EXPIRED (u103)`**: Proposal's voting period has ended.
- **`ERR-INSUFFICIENT-FUNDS (u104)`**: Insufficient treasury funds for requested action.
- **`ERR-ZERO-AMOUNT (u105)`**: Amount provided must be greater than zero.
- **`ERR-INVALID-STATUS (u106)`**: Proposal status is invalid for the requested action.
- **`ERR-SELF-DELEGATION (u107)`**: Delegating votes to oneself is not allowed.
- **`ERR-INVALID-TITLE-LENGTH (u108)`**: Proposal title length is invalid.
- **`ERR-INVALID-DESC-LENGTH (u109)`**: Proposal description length is invalid.

---

## Usage

### **Joining the DAO**
1. Use `join-dao` to become a member by staking the minimum amount of STX.
2. Earn reputation points to gain voting rights and participate actively.

### **Submitting a Proposal**
1. Call `submit-proposal` with the title, description, and requested funding amount.
2. Proposal will be active for voting during the defined `VOTING_PERIOD`.

### **Voting on Proposals**
1. Use `cast-vote` to support or reject a proposal.
2. Optionally delegate your vote to another member using `delegate-vote`.

### **Executing Approved Proposals**
1. After the `VOTING_PERIOD`, call `execute-proposal` if the proposal has sufficient approvals.
2. Funds will be transferred to the proposer.

---

## Security Considerations
- **Membership Verification**: Only DAO members can participate in proposals and voting.
- **Reputation System**: Tracks member contributions and enforces fair participation.
- **Proposal Expiry**: Votes on expired proposals are invalid.
- **Treasury Protection**: Funds cannot be withdrawn without sufficient reputation or proposal approval.

---

## Future Enhancements
- Add slashing mechanisms for malicious members.
- Introduce tiers of membership based on reputation.
- Enable DAO treasury investments for growth.

This contract provides a solid foundation for decentralized governance and local development initiatives.