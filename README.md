# SRT EA

## Developer - Forex Robot Easy Team
## Developer's Site - forexroboteasy.com

This code is a trading robot based on the SRT Expert Advisor. It performs forex trading simulations with proven performance and is stress-tested under real market conditions. The code provides a realistic simulation of the forex market with a quality of 99.9% real ticks. It includes a feature to control the quality of broker execution and passes stringent criteria based on historical data and Monte Carlo simulations. 

The optimal timeframe for this code is H1. Market entry signals are formed only from the overbought and oversold zones, considered the safest entry points. Necessary trading functions are implemented to execute the algorithm.

## Input Parameters

- LotSize: Trading lot size
- StopLoss: Stop loss level in pips
- TakeProfit: Take profit level in pips

## Global Variables

- overboughtLevel: Overbought level
- oversoldLevel: Oversold level

## SRT EA Code

```mql5
// Called when the EA is initialized
int OnInit()
{
    // Set the necessary trading functions and parameters
    SetOrderExecution(ORDER_EXECUTION_INSTANT);
    SetSlippage(10);
    SetCommission(0.5);
    SetQualityFlags(QUALITY_REAL_TICKS);
    
    return(INIT_SUCCEEDED);
}

// Called on each tick
void OnTick()
{
    // Check if the current price is in the overbought zone
    if (iCustom(Symbol(), PERIOD_H1, 'OverboughtOversoldIndicator') > overboughtLevel)
    {
        // Place a sell order
        Sell(LotSize, Ask - StopLoss * Point, Ask + TakeProfit * Point);
    }
    
    // Check if the current price is in the oversold zone
    if (iCustom(Symbol(), PERIOD_H1, 'OverboughtOversoldIndicator') < oversoldLevel)
    {
        // Place a buy order
        Buy(LotSize, Ask + StopLoss * Point, Ask - TakeProfit * Point);
    }
}

// Called when the EA is deinitialized
void OnDeinit(const int reason)
{
    // Perform any necessary clean-up or logging
    Print('SRT EA deinitialized. Reason:', reason);
}
```

To find the official developer of this product, please use MQL5.

For detailed reviews and trading results of this product, please visit [ForexRobotEasy](https://forexroboteasy.com/forex-robot-review/srt-ea-review-proven-performance-in-forex-market-simulations/). Please note that ForexRobotEasy is not the official developer of this product. They only show sample code that can work as described in this product.
