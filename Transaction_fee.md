# Transaction Fee Configuration for Substrate Blockchain

This file outlines the configuration of the `pallet_transaction_payment` for handling transaction fees in our Substrate-based blockchain. The configuration aims to balance throughput, prevent network spam, and prioritize critical operations through dynamic fee adjustment.

## Overview

The `pallet_transaction_payment` is responsible for the fee calculation of transactions processed on the network. It supports dynamic fee adjustment based on network congestion and block fullness, aiming to maintain a target block fullness for optimal network performance.

## Configuration Parameters

Below are the key parameters used in the configuration of the transaction payment pallet:

- `TransactionByteFee`: Fee charged per byte of the transaction data. Set to 10 milli-cents per byte.
- `OperationalFeeMultiplier`: Multiplier for fees related to operational transactions, set to 5x the normal fee rate.
- `TargetBlockFullness`: Target utilization percentage of each block, set to 25%.
- `AdjustmentVariable`: Rate of adjustment for the dynamic fee multiplier based on network conditions.
- `MinimumMultiplier`: Lower bound for the dynamic fee multiplier, ensuring fees remain reasonable during low congestion.
- `MaximumMultiplier`: Upper bound for the fee multiplier to prevent excessive fees during high congestion.

## Implementation

The implementation in the runtime includes the following configurations:

```rust
parameter_types! {
    pub const TransactionByteFee: Balance = 10 * MILLICENTS;
    pub const OperationalFeeMultiplier: u8 = 5;
    pub const TargetBlockFullness: Perquintill = Perquintill::from_percent(25);
    pub AdjustmentVariable: Multiplier = Multiplier::saturating_from_rational(1, 100_000);
    pub MinimumMultiplier: Multiplier = Multiplier::saturating_from_rational(1, 1_000_000_000u128);
    pub MaximumMultiplier: Multiplier = Bounded::max_value();
}

impl pallet_transaction_payment::Config for Runtime {
    type RuntimeEvent = RuntimeEvent;
    type OnChargeTransaction = CurrencyAdapter<Balances, DealWithFees>;
    type OperationalFeeMultiplier = OperationalFeeMultiplier;
    type WeightToFee = IdentityFee<Balance>;
    type LengthToFee = ConstantMultiplier<Balance, TransactionByteFee>;
    type FeeMultiplierUpdate = TargetedFeeAdjustment<
    Self,
    TargetBlockFullness,
    AdjustmentVariable,
    MinimumMultiplier,
    MaximumMultiplier,
>;
```

## Usage

The configured `pallet_transaction_payment` enables the network to dynamically adjust transaction fees based on the real-time state of the blockchain. Here are key points regarding its usage:

- **Transaction Costs**: Fees are calculated based on transaction size and complexity, with operational transactions incurring a higher fee.
- **Dynamic Adjustment**: The network adjusts fees to aim for the configured target block fullness, enhancing network resilience against spam and overloading.

## Deployment

To deploy these settings in a Substrate node, ensure that your node's runtime includes the `pallet_transaction_payment` with the provided configuration. Compile the node with the latest changes:

```bash
cargo build --release
```

