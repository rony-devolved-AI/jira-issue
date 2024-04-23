```rs
parameter_types! {
	pub const ProposalBond: Permill = Permill::from_percent(5);
	pub const ProposalBondMinimum: Balance = 1 * ARGO;
	pub const SpendPeriod: BlockNumber = 1 * DAYS;
	pub const Burn: Permill = Permill::from_percent(50);
	pub const TipCountdown: BlockNumber = 1 * DAYS;
	pub const TipFindersFee: Percent = Percent::from_percent(20);
	pub const TipReportDepositBase: Balance = 1 * ARGO;
	pub const DataDepositPerByte: Balance = 1 * CENTS;
	// 5EYCAe5ijiYfyeZ2JJCGq56LmPyNRAKzpG4QkoQkkQNB5e6Z
	pub const TreasuryPalletId: PalletId = PalletId(*b"py/trsry");
	pub const MaximumReasonLength: u32 = 300;
	pub const MaxApprovals: u32 = 100;
	pub const MaxBalance: Balance = Balance::max_value();
}

impl pallet_treasury::Config for Runtime {
	type PalletId = TreasuryPalletId;
	type Currency = Balances;
	type ApproveOrigin = EitherOfDiverse<
		EnsureRoot<AccountId>,
		pallet_collective::EnsureProportionAtLeast<AccountId, CouncilCollective, 3, 5>,
	>;
	type RejectOrigin = EitherOfDiverse<
		EnsureRoot<AccountId>,
		pallet_collective::EnsureProportionMoreThan<AccountId, CouncilCollective, 1, 2>,
	>;
	type RuntimeEvent = RuntimeEvent;
	type OnSlash = ();
	type ProposalBond = ProposalBond;
	type ProposalBondMinimum = ProposalBondMinimum;
	type ProposalBondMaximum = ();
	type SpendPeriod = SpendPeriod;
	type Burn = Burn;
	type BurnDestination = ();
	type SpendFunds = Bounties;
	type WeightInfo = pallet_treasury::weights::SubstrateWeight<Runtime>;
	type MaxApprovals = MaxApprovals;
	type SpendOrigin = EnsureWithSuccess<EnsureRoot<AccountId>, AccountId, MaxBalance>;
}

```


# Substrate Treasury Pallet Configuration

This document details the configuration parameters for the `pallet_treasury` module within a Substrate-based blockchain. The treasury pallet is responsible for managing the community treasury, allowing funds to be spent on public goods, development, and other initiatives that benefit the network.

## Configuration Parameters

### 1. `ProposalBond`
- **Description**: Specifies the percentage of the proposal value that must be bonded when submitting a spending proposal.
- **Value**: `5%`
- **Impact**: Ensures stakeholders have a vested interest in the proposals they submit by locking up funds as collateral.

### 2. `ProposalBondMinimum`
- **Description**: Sets the minimum bond amount required for a treasury proposal.
- **Value**: `1 ARGO`
- **Impact**: Guarantees a minimum bond regardless of the proposal size.

### 3. `SpendPeriod`
- **Description**: Defines the interval at which the treasury can make spending decisions.
- **Value**: `1 DAY`
- **Impact**: Controls the frequency of treasury spending, allowing for daily funding decisions.

### 4. `Burn`
- **Description**: Percentage of unspent treasury funds that are burned.
- **Value**: `50%`
- **Impact**: Reduces excess liquidity in the treasury by destroying half of the unspent funds, acting as a deflationary mechanism.

### 5. `TipCountdown`
- **Description**: Time period required for a tip proposal to be finalized.
- **Value**: `1 DAY`
- **Impact**: Allows time for evaluation and finalization of community tips, ensuring proper governance.

### 6. `TipFindersFee`
- **Description**: Fee percentage that goes to the finder of a tip.
- **Value**: `20%`
- **Impact**: Incentivizes community members to propose tips by rewarding them with a portion of the tip amount.

### 7. `TipReportDepositBase`
- **Description**: Deposit required for making a tip report.
- **Value**: `1 ARGO`
- **Impact**: Minimizes spam by requiring a deposit for tip submissions.

### 8. `DataDepositPerByte`
- **Description**: Cost per byte of data stored on-chain.
- **Value**: `1 CENT`
- **Impact**: Encourages efficient data usage on-chain by charging for storage.

### 9. `TreasuryPalletId`
- **Description**: Unique identifier for the treasury pallet.
- **Value**: `py/trsry`
- **Impact**: Ensures that the treasury's storage does not conflict with other pallets.

### 10. `MaximumReasonLength`
- **Description**: Maximum length of the reason field in treasury proposals.
- **Value**: `300 characters`
- **Impact**: Keeps proposal descriptions concise.

### 11. `MaxApprovals`
- **Description**: Maximum number of spending proposals approved per period.
- **Value**: `100`
- **Impact**: Controls the flow of treasury spending by limiting the number of approvals.

### 12. `MaxBalance`
- **Description**: Maximum balance that the `SpendOrigin` can manage.
- **Value**: Maximum value of `Balance` type
- **Impact**: Imposes no upper limit on the balance managed by the `SpendOrigin`.

## Implementation

The treasury configuration is implemented through the `pallet_treasury::Config` for the runtime, ensuring integration with other runtime components and adherence to governance mechanisms such as proposal approval and rejection origins.

### Key Interfaces

- **`ApproveOrigin` and `RejectOrigin`**: Define the governance rules for who can approve or reject proposals.
- **`SpendFunds`**: Links to the `Bounties` pallet to enable funding for bounties from the treasury.
- **`WeightInfo`**: Facilitates calculation of the computational cost for treasury operations.
- **`SpendOrigin`**: Specifies who can propose treasury spendings, subject to checks for success conditions and balance limits.

This configuration ensures a robust framework for managing the treasury in a Substrate-based blockchain, aligning financial incentives with community-driven governance.
