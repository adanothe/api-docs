**API endpoint:** [https://public.adanothe.com/graphql](https://public.adanothe.com/graphql)

### Query Examples

### Get Validator Information

**Query:**
```graphql
query getValidator($address: String!) {
  getValidator(address: $address) {
    treasury
    nodeAddress
    oracleAddress
    enode
    commissionRate
    bondedStake
    unbondingStake
    unbondingShares
    selfBondedStake
    selfUnbondingShares
    selfUnbondingStakeLocked
    liquidContract
    liquidSupply
    registrationBlock
    totalSlashed
    jailReleaseBlock
    provableFaultCount
    consensusKey
    state
    moniker
    keybase
    description
    website
    email
    github
    twitter
    discord
    telegram
    logo_url
    blockValidated
    oracleVote
  }
}
```
This query is used to retrieve detailed information about a specific validator based on its validator address (`address`).

 *filter parameter:*
- `ACTIVE`
- `CANDIDATE`
- `INACTIVE`

### Get All Validators with Filter

**Query:**
```graphql
query allValidator($limit: Int, $offset: Int, $filter: ValidatorFilter) {
  allValidator(limit: $limit, offset: $offset, filter: $filter) {
    validators {
      treasury
      nodeAddress
      oracleAddress
      enode
      commissionRate
      bondedStake
      unbondingStake
      unbondingShares
      selfBondedStake
      selfUnbondingShares
      selfUnbondingStakeLocked
      liquidContract
      liquidSupply
      registrationBlock
      totalSlashed
      jailReleaseBlock
      provableFaultCount
      consensusKey
      state
      moniker
      keybase
      description
      website
      email
      github
      twitter
      discord
      telegram
      logo_url
      blockValidated
      oracleVote
    }
    totalCount
  }
}
```
This query is used to retrieve a list of all validators with options to apply a limit (`limit`), offset (`offset`), and filter based on the validator state (`filter`).

### Get Network Details

**Query:**
```graphql
query {
  network {
    blockHeight
    epoch
    epochBlock
    totalSupply
    bondedSupply
    unbondedSupply
    maxValidator
    unbondedPercentage
    bondedPercentage
    unbondingPeriod
    blockPeriod
    seatPrice
    lastEpochTime
    reserve
  }
}
```
This query is used to retrieve detailed information about the network, including block height, epoch, total supply, bonded and unbonded supply, and other relevant information.

### Get Committee Members

**Query:**
```graphql
query {
  getCommittee {
    addr
    votingPower
    consensusKey
  }
}
```
This query is used to retrieve the list of committee members, including their addresses, voting power, and consensus keys.

### Get Block Details

**Query:**
```graphql
query getBlockDetail($blockHeight: Int!) {
  blockDetail(blockHeight: $blockHeight) {
    consensus {
      difficulty
      gasLimit
      gasUsed
      hash
      minerHash
      nonce
      number
      parentHash
      size
      timestamp
      baseFeePerGas
      burntFees
      priorityFees
      totalDifficulty
      transactionCount
      transactionHashes
    }
  }
}
```
This query is used to retrieve details of a specific block based on its height (`blockHeight`), including consensus information and transactions.

### Get Oracle Round Data for a Specific Symbol

**Query:**
```graphql
query getOracle($symbol: String!) {
  getOracle(symbol: $symbol) {
    symbol
    price
    timestamp
    round
    success
  }
}
```
This query is used to retrieve oracle round data for a specific symbol (`symbol`). Available oracle symbols include:
- `AUD-USD`
- `CAD-USD`
- `EUR-USD`
- `GBP-USD`
- `JPY-USD`
- `SEK-USD`
- `ATN-USDC`
- `NTN-USDC`
- `NTN-ATN`

### Get Latest Oracle Round Data

**Query:**
```graphql
query {
  latestRoundData {
    symbol
    price
    timestamp
    round
    success
  }
}
```
This query is used to retrieve the latest oracle round data for all available symbols.

### Get Oracle Round Data by Symbol and Round

**Query:**
```graphql
query getRoundData($symbol: String!, $round: String!) {
  getRoundData(symbol: $symbol, round: $round) {
    symbol
    price
    timestamp
    round
    success
  }
}
```
This query is used to retrieve oracle round data based on the symbol (`symbol`) and round (`round`).

### Get Oracle Parameters

**Query:**
```graphql
query {
  oracleParam {
    precision
    round
    symbols
    votePeriod
    voters
  }
}
```
This query is used to retrieve oracle parameters, including precision, round, symbols, vote period, and voters.

### Get Delegators of a Specific Validator

**Query:**
```graphql
query getDelegators($validatorAddress: String!, $limit: Int, $offset: Int) {
  getDelegators(validatorAddress: $validatorAddress, limit: $limit, offset: $offset) {
    delegators {
      delegator
      amount
    }
    totalCount
  }
}
```
This query is used to retrieve the list of delegators for a specific validator based on the validator address (`validatorAddress`), with options to apply a limit (`limit`) and offset (`offset`).

### Get Power Transactions of a Specific Validator

**Query:**
```graphql
query getPowertx($validatorAddress: String!, $limit: Int, $offset: Int) {
  getPowertx(validatorAddress: $validatorAddress, limit: $limit, offset: $offset) {
    transactions {
      delegator
      selfBonded
      amount
      block_number
      epoch
      transaction_hash
      timestamp
      event_type
    }
    totalCount
  }
}
```
This query is used to retrieve the list of power transactions for a specific validator based on the validator address (`validatorAddress`), with options to apply a limit (`limit`) and offset (`offset`).

### Get Delegate List of a Specific Delegator

**Query:**
```graphql
query delegateList($delegatorAddress: String!, $limit: Int, $offset: Int) {
  delegateList(delegatorAddress: $delegatorAddress, limit: $limit, offset: $offset) {
    delegates {
      validator
      amount
      moniker
      unclaimedRewards {
        ATN
        NTN
      }
    }
    totalCount
  }
}
```
This query is used to retrieve the delegate list of a specific delegator based on the delegator address (`delegatorAddress`), with options to apply a limit (`limit`) and offset (`offset`).

### Get Account Balance

**Query:**
```graphql
query getAccountBalance($address: String!) {
  accountBalance(address: $address) {
    address
    balances {
      symbol
      balance
    }
  }
}
```
This query is used to retrieve the balance of a specific account based on its address (`address`), including the balance for each token held by the account.

### Get Account Transactions

**Query:**
```graphql
query getAccountTransactions($address: String!) {
  getAccountTransactions(address: $address) {
    method
    hash
    type
    block
    from
    to
    value
    fee
    token
    symbol
  }
}
```
This query is used to retrieve the list of transactions for a specific account based on its address (`address`).

