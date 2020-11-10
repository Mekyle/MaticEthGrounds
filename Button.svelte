<script>
		//The smart contract details
		const contractAddress = "0xcbd2a0814ffac11f8c1a9db9cad8bf4b5d3b82fd";
		const contractAbi = [
		  {
		    constant: false,
		    inputs: [{ name: "_name", type: "string" }],
		    name: "setValue",
		    outputs: [{ name: "", type: "string" }],
		    payable: false,
		    stateMutability: "nonpayable",
		    type: "function"
		  },
		  {
		    constant: true,
		    inputs: [],
		    name: "getValue",
		    outputs: [{ name: "", type: "string" }],
		    payable: false,
		    stateMutability: "view",
		    type: "function"
		  },
		  {
		    constant: true,
		    inputs: [],
		    name: "name",
		    outputs: [{ name: "", type: "string" }],
		    payable: false,
		    stateMutability: "view",
		    type: "function"
		  }
		];

		let account;
		let balance;
		import { ethers, utils } from "ethers";

		async function connectToMetamask() {
		  if (
		    typeof window.ethereum !== "undefined" ||
		    typeof window.web3 !== "undefined"
		  ) {
		    // Web3 browser user detected. You can now use the provider.
		    const accounts = await window.ethereum.enable();
		    // const curProvider = window['ethereum'] || window.web3.currentProvider

		    const provider = new ethers.providers.Web3Provider(window.ethereum);

		    console.log("accounts: ", accounts);
		    console.log("provider: ", provider);

		    const signer = provider.getSigner();
		    account = accounts[0];

		    balance = await provider.getBalance(account);
		    balance = ethers.utils.formatEther(balance);

		    return balance;
		    return account;
		  }
		}
</script>

<style>
	button {
	  background: #ff3e00;
	  color: white;
	  border: none;
	  padding: 8px 12px;
	  border-radius: 2px;
	}
</style>

<button on:click={connectToMetamask()}>Connect to MetaMask</button>

<h1>Hello {account}</h1>
<h2>Your balance is {balance} Eth</h2>