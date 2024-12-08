const { ethers } = require("ethers");

// اطلاعات شبکه
const provider = new ethers.providers.JsonRpcProvider("https://<RPC-URL>");
const wallet = new ethers.Wallet("<PRIVATE_KEY>", provider);

// اطلاعات قرارداد
const contractAddress = "<CONTRACT_ADDRESS>";
const abi = [<CONTRACT_ABI>];  // جایگزین با ABI قرارداد

// اتصال به قرارداد
const contract = new ethers.Contract(contractAddress, abi, wallet);

async function unstakeTokens() {
    try {
        const tx = await contract.unstake(); // متد دقیق ممکن است نام دیگری داشته باشد
        console.log("Transaction submitted:", tx.hash);
        await tx.wait();
        console.log("Unstake successful!");
    } catch (error) {
        console.error("Error unstaking tokens:", error);
    }
}

unstakeTokens();
