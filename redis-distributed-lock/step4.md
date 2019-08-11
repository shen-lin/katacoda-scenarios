Find the 'Start Web App' tab next to the 'Terminal' tab.

Click on this tab twice to open the frontend web app in two browser tabs.

The REST handler of the webapp reads the current balance stored in Redis, adds the input value of the deposit field to the balance, and finally writes the updated balance to Redis storage. The REST handler was implemented in a way so that 10 seconds sleep takes place after reading the balance and before 
adding the deposit input to the balance value. Thus, if you perform another deposit in a second browser tab within 10 seconds, the following is going
to happen without distributed lock.

- Browser tab 1: Deposit 5
- Browser tab 1: Read balance value 0
- Browser tab 1: Sleep for 10 seconds
- Browser tab 2: Deposit 3
- Browser tab 2: Read balance value 0
- Browser tab 2: Sleep for 10 seconds
- Browser tab 1: Update new balance 5 + 0 = 5
- Browser tab 1: Write new balance 5 back to Redis
- Browser tab 2: Update new balance 3 + 0 = 3
- Browser tab 2: Write new balance 3 back to Redis
- After two deposits, the eventual balance has incorrect value 3.

The distributed lock used in this scenario makes sure only one process is accessing the balance resource. 

Note: 

Some enhancements are required on the redis clients. The client holding the lock should keep extend it if it is still accessing the resource when its lock is getting expired. And if the client failed to extend the lock, it shouldn't access the resource any more.