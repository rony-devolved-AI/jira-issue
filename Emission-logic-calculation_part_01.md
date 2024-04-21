# Emission Logic Calculation


### MD RAISUL ISLAM RONY
### Blockchain Developer @ Devolved_Ai



##  Concepts

```rs

const REWARD_CURVE: PiecewiseLinear<'static> = curve!(
		min_inflation: 0_025_000,
		max_inflation: 0_100_000,
		ideal_stake: 0_500_000,
		falloff: 0_050_000,
		max_piece_count: 40,
		test_precision: 0_005_000,
	);
```



1. **_Min-Inflation_** This is the minimum amount of new tokens that will be created and given as rewards to validators , regardless of hom many tokens are staked .

2. **_Max-Inflation_** This is the maximum amount of new tokens that will be created and given as rewards to validators . The maximum amount only reached if the perfect amount of tokens get staked . as defined by `ideal_stake` . 

3. **_ideal_stake_** This is the target proportion of the total tokens in the system that should be staked. If this exact amount is staked, validators receive the maximum inflation reward .
4. **_falloff_** This determines `how quickly reward changes` If the `actual staked amount` is different from `ideal_stake` . A `high` falloff means the reward `decrease`  `more` sharply as the staked amount `moves away from the ideal target` .

5. **_max_piece_count_**  This determines the `complexity` of the inflation curve. A `higher number` means the curve is `more detailed` and can `more accurately` give rewards, but it also requires `more computational` resources to calculate.

6. **_test_precision_**  This is the `allowable margin` of error when testing the curve to ensure it's working correctly. A `smaller number` means the tests are more strict and the curve must be `more precise`.