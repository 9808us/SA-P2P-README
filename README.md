# SUPERALGOS OUTGOING AND INCOMING SIGNALS

PREFACE/INTRODUCTION TO BE WRITTEN

TABLE OF CONTEXT

---

# OUTGOING SIGNALS

To be able to send signals using the built in features of Superalgos, you must first prepare your User Profile with specific nodes. You will also need a dedicated Github Repo as well as trading system and workspace. 

### User profile

Add the following to your user profile, you might have to add the Network project and it's plugins to the workspace you are using.

### Add...

- User Apps > Server Apps > Task Server
- User Apps > Server Apps > Social Trading Server *(Unsure if needed....)*
- User Bots > Social Trading Bots > Social Trading Bot > Available Signals > Trading System Signals > Trading Strategy Signals
- User Bots > Social Trading Bots > Social Trading Bot > Available Storage
- User Storage > Github Storage > Github Storage Container
- P2P Network Nodes > P2P Network Node

### Social Trading Bot

Under the Social Trading Bot node in your profile you must
- Reference Available Storage Reference to the Github Storage Container of choice
- Edit/check Trading Strategy Signals
	- Here you setup which signals you want to send, some more details are found under the section "Trading System"

	
### Github Storage Container

Your signals have to save somewhere, in the setup we are using a dedicated github repo that will host the files, don't worry they are encrypted :)

Under the Github Storage Container
- Edit codeName to a unique identifier
- Edit githubUserName to your github user account
- Edit repositoryName to your github repository where you'll save the trading signals

You must also add a JSON-file to your Superalgos folder, under Superalgos/My-Secrets create a file called "ApisSecrets.json", enter the following details in the following format.

```
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
```	

### P2P Network Node

It is good pratice *(and maybe required? unsure...)* to run a network node. 

Under the P2P Network Node in your user profile 
- Add Network Services > Trading Signals
- Reference P2P Network Reference to the network of choice (mainnet or testnet for public signals or create your own permissioned P2P network)

**Using Tesnet will at the moment result in interference with the Machine Learning Project, as they are using Testnet. Should not happen, but seems to be a bug there.**

Whatever network you choose to send signals over, the Environment.js file under /Superalgos, has to be change to the same network type and network codename (don't forget to restart Superalgos). 

The following was used for Permissioned P2P Network.
```
...
DESKTOP_TARGET_NETWORK_TYPE: 'Permissioned P2P Network',
DESKTOP_TARGET_NETWORK_CODENAME: 'BlaaSignals',
TASK_SERVER_TARGET_NETWORK_TYPE: 'Permissioned P2P Network',
TASK_SERVER_TARGET_NETWORK_CODENAME: 'BlaaSignals',
...
```
	
**NOTE:** There needs to be network nodes running for the choosen network, if permissioned p2p you need to run your own node. 
	

### Signing Account 

After you are done with your changes to your user profile, you must sign them. This is to ensure that you are you and noone else. This is done with the Profile Constructor (poart of the Governance project). 

- Reference your User Profile to the profile constructor
- Profile contructor > Installing signing account
- User Profile > Save Plugin
- **PR your updated profile**

	

### Trading System

Nest up is to setup the trading system! 

- Reference Trading System Outgoing Signal Reference to Trading System Signal (Under Socical Trading Bot > Available Signals)
- Add outgoing signals for choice, you can add as many or as few that you wish
	- If signals are based on formulas, you can if you wish add Signal Context Formula, to even further edit the value being sent. 
- Reference all outgoing signals to the correct Signal under Trading Strategy Signals.
	- For instance, a Market Buy Signal in the trading system goes to the Market Buy Signal under Trading Strategy Signals. 

Signals cannot be used as a conditions on it's own, to use signals as a true/false statement, enter the following as a conditions to the event: 

```
if (signals !== undefined && signals.length > 0) {
    true
} else {
    false
}
```

### P2P Network Node

Almost there, you need to add a couple of nodes before you run your trading task (either Testing Trading Tasks or Production Trading Tasks).

- Add Task Server Reference on Task
- Reference Task Server Reference to the a free Task Server in the User Profile 
- Add Social Trading Bot Reference to Trading Bot Instance
- Reference Social Trading Bot Reference to the correct Social Trading Bot in User Profile (the one that will send your signals)


---

# INCOMING SINGALS 
## User profile
- Add User Apps > Server Apps > Task Server
- Add User Bots > Social Trading Bots > Social Trading Bot > Available Signals > Incoming Signals

## Incoming Signals

Here you add what signals you want to use in your trading system. 
You reference them from the user profile that is sending the signals (under available signals > trading system signals > trading strategy signals)
Note: You have to add the trading system signal, otherwise the candles won't sync. 


## Signing Account

Reference your User Profile to the profile constructor
Profile contructor > Installing signing account

-PR your updated profile


## P2P Network Node (Either Testing Trading Tasks or Production Trading Tasks)

Add Task Server Reference on Task
Reference Task Server Reference to the correct Task Server in the User Profile
Add Social Trading Bot Reference to Trading Bot Instance
Reference Social Trading Bot Reference to the correct Social Trading Bot in User Profile


## NOTE:

Whatever network the signals are being sent over, the Environment.js file under /Superalgos, has to be change to the same network type and network codename. 
The following was used for Permissioned P2P Network.

```
DESKTOP_TARGET_NETWORK_TYPE: 'Permissioned P2P Network',
DESKTOP_TARGET_NETWORK_CODENAME: 'BlaaSignals',
TASK_SERVER_TARGET_NETWORK_TYPE: 'Permissioned P2P Network',
TASK_SERVER_TARGET_NETWORK_CODENAME: 'BlaaSignals',
```
