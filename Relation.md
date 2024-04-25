#  Total Emission Calculation

> **Per Block =.90 AGC**
>> **45% Goes to Staking and 55% goes to PoV**
>>> **Out of Staking 1 % Goes to Treasury and Rest Goes to validator as Reward**

>>>**Out of PoV pool 1% goes to Treasury Rest Goes to Validator as Reward**


```rs
impl OnUnbalanced<NegativeImbalance> for DealWithFees {
	fn on_unbalanceds<B>(mut fees_then_tips: impl Iterator<Item = NegativeImbalance>) {
		if let Some(fees) = fees_then_tips.next() {
			// for fees, 80% to treasury, 20% to author
			let mut split = fees.ration(80, 20);
			if let Some(tips) = fees_then_tips.next() {
				// for tips, if any, 80% to treasury, 20% to author (though this can be anything)
				tips.ration_merge_into(80, 20, &mut split);
			}
			Treasury::on_unbalanced(split.0);
			Author::on_unbalanced(split.1);
		}
	}
}
```
>>> **As per code implementation for Total Gas Fee , 80 % goes to treasury and 20 to validator .** 


> For `inflation` and `payout` you will find the paritytech code in _https://github.com/paritytech/substrate/blob/master/frame/staking/src/inflation.rs#L32-L50_

> For  calculating validator reward between `max inflation` and `min inflation` visit _https://github.com/paritytech/substrate/blob/master/frame/staking/reward-fn/src/lib.rs_
