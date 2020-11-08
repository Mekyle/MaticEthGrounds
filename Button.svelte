<script>
	import WalletConnectProvider from "@maticnetwork/walletconnect-provider";
	import Web3 from "web3";
	import Matic from "maticjs";

	const maticProvider = new WalletConnectProvider({
	  host: `https://rpc-mumbai.matic.today`,
	  callbacks: {
	    onConnect: console.log("connected"),
	    onDisconnect: console.log("disconnected!")
	  }
	});

	const ropstenProvider = new WalletConnectProvider({
	  host: `https://ropsten.infura.io/v3/70645f042c3a409599c60f96f6dd9fbc`,
	  callbacks: {
	    onConnect: console.log("connected"),
	    onDisconnect: console.log("disconnected")
	  }
	});

	const maticWeb3 = new Web3(maticProvider)
	const ropstenWeb3 = new Web3(ropstenProvider)

	const myContractAddress = 

	const myContractInstance = new maticWeb3.eth.Contract(myContractAbi, myContractAddress)

	//  Enable session (triggers QR Code modal)
	async function metamask() {
	  await web3Provider.enable();
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

<button on:click= {metamask}>
  Clicked 
</button>