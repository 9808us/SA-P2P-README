# SA-P2P-README



# OUTGOING SINGALS
_______________________________________________________________________________________________________________________________
User profile
--------------------
Add User Apps > Server Apps > Task Server
Add User Apps > Server Apps > Social Trading Server (Unsure if needed....)
Add User Bots > Social Trading Bots > Social Trading Bot > Available Signals > Trading System Signals > Trading Strategy Signals
Add User Bots > Social Trading Bots > Social Trading Bot > Available Storage
Add User Storage > Github Storage > Github Storage Container
Add P2P Network Nodes > P2P Network Node

	Social Trading Bot
	--------------------
	Reference Available Storage Reference to the Github Storage Container of choice
	Edit/check Trading Strategy Signals
		Here you setup which signals you want to send, some more details are found under the section "Trading System"

	
	Github Storage Container
	--------------------	
	Edit codeName to a unique identifier
	Edit githubUserName to your github user account
	Edit repositoryName to your github repository where you'll save the trading signals

	Under Superalgos/My-Secrets create a file called "ApisSecrets.json", enter the following details in the following format.

	{
		"secrets": [
		{
			"nodeCodeName": "codeName-that-you-have-chosen-in-github-storage-container",
			"apiToken": "your-api-token-from-github"
		},
		{
			"nodeCodeName": "codeName-that-you-have-chosen-in-github-storage-container-number2",
			"apiToken": "your-api-token-from-github"
		}
		]
	}
	

	P2P Network Node
	--------------------
	Add Network Services > Trading Signals
	Reference P2P Network Reference to the network of choice (mainnet or testnet for public signals or create your own permissioned P2P network)

	NOTE: Using Tesnet will at the moment result in interference with the Machine Learning Project, as they are using Testnet. Should not happen, but seems to be a bug there.
	
	NOTE: There need to be network nodes running for the choosen network, if permissioned p2p you need to run your own node. 

	NOTE:
	Whatever network you choose to send signals over, the Environment.js file under /Superalgos, has to be change to the same network type and network codename. 
	The following was used for Permissioned P2P Network.
	DESKTOP_TARGET_NETWORK_TYPE: 'Permissioned P2P Network',
	DESKTOP_TARGET_NETWORK_CODENAME: 'BlaaSignals',
	TASK_SERVER_TARGET_NETWORK_TYPE: 'Permissioned P2P Network',
	TASK_SERVER_TARGET_NETWORK_CODENAME: 'BlaaSignals',
	
	

	Signing Account 
	--------------------
	Reference your User Profile to the profile constructor
	Profile contructor > Installing signing account



####	PR your updated profile

	

Trading System
--------------------
Reference Trading System Outgoing Signal Reference to Trading System Signal (Under Socical Trading Bot > Available Signals)
Add outgoing signals for choice, you can add as many or as few that you wish
	If signals are based on formulas, you can if you wish add Signal Context Formula, to even further edit the value being sent. 
Reference all outgoing signals to the correct Signal under Trading Strategy Signals.

Signals cannot be used as a conditions on it's own, to use signals as a true/false statement, enter the following as a conditions to the event: 
if (signals !== undefined && signals.length > 0) {
    true
} else {
    false
}


LAN Network Node (Either Testing Trading Tasks or Production Trading Tasks)
--------------------
Add Task Server Reference on Task
Reference Task Server Reference to the a free Task Server in the User Profile 
Add Social Trading Bot Reference to Trading Bot Instance
Reference Social Trading Bot Reference to the correct Social Trading Bot in User Profile (the one that will send your signals)





INCOMING SINGALS 
_______________________________________________________________________________________________________________________________
User profile
--------------------
Add User Apps > Server Apps > Task Server
Add User Bots > Social Trading Bots > Social Trading Bot > Available Signals > Incoming Signals

	Incoming Signals
	--------------------
	Here you add what signals you want to use in your trading system. 
	You reference them from the user profile that is sending the signals (under available signals > trading system signals > trading strategy signals)
	Note: You have to add the trading system signal, otherwise the candles won't sync. 


	Signing Account 
	--------------------
	Reference your User Profile to the profile constructor
	Profile contructor > Installing signing account


####	PR your updated profile


LAN Network Node (Either Testing Trading Tasks or Production Trading Tasks)
--------------------
Add Task Server Reference on Task
Reference Task Server Reference to the correct Task Server in the User Profile
Add Social Trading Bot Reference to Trading Bot Instance
Reference Social Trading Bot Reference to the correct Social Trading Bot in User Profile


NOTE:
Whatever network the signals are being sent over, the Environment.js file under /Superalgos, has to be change to the same network type and network codename. 
The following was used for Permissioned P2P Network.
DESKTOP_TARGET_NETWORK_TYPE: 'Permissioned P2P Network',
DESKTOP_TARGET_NETWORK_CODENAME: 'BlaaSignals',
TASK_SERVER_TARGET_NETWORK_TYPE: 'Permissioned P2P Network',
TASK_SERVER_TARGET_NETWORK_CODENAME: 'BlaaSignals',
	
