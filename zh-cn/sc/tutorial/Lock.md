# 智能合约示例——Lock（锁仓合约）

```c#
public class Lock : FunctionCode
{
    public static bool Main(uint timestamp, byte[] pubkey, byte[] signature)
    {
        Header header = Blockchain.GetHeader(Blockchain.GetHeight());
<<<<<<< HEAD
        if (timestamp > header.Timestamp) return false;
=======
        if (header.Timestamp < timestamp)
            return false;
>>>>>>> e5e43331cd35f87f336ded6b98df4277306e0359
        return VerifySignature(pubkey, signature);
    }
}
```

该合约实现了一个这样的功能：指定一个时间戳（timestamp），当区块链系统的时间到达该指定的时间之前，任何人也不能从该合约中将资金取出，当区块链系统的时间过了指定的时间后，合约持有者可以将资金取出。

<<<<<<< HEAD
代码中通过区块链中最新区块的时间来获得当前时间（误差大约在15秒以内）。详情可参考 [Blockchain类](../fw/dotnet/AntShares/Blockchain.md)，   [Header类](../fw/dotnet/AntShares/Header.md)。
=======
代码中通过区块链中最新区块的时间来获得当前时间（误差大约在 15 秒以内）。详情可参考 [Blockchain 类](../fw/dotnet/neo/Blockchain.md)，   [Header 类](../fw/dotnet/neo/Header.md)。

该合约继承于 FunctionCode，是用来部署到区块链上供其它人调用的，如果想在本地部署锁仓合约，请参考 [锁仓合约的部署](Lock2.md)。
>>>>>>> e5e43331cd35f87f336ded6b98df4277306e0359
