# Algorand Lottery:

Tracked Quantities:
- User => Amount Spent
- Users
- Total Pool
- Secondary Receiver => Votes
- Secondary Receiver => Name
- Secondary Receiver => Description
- Secondary Receiver => URI
- Secondary Receivers
- Votes to Increase within Period
- Votes to Decrease within Period
- Previous Winner
- Previous Winner Percent
- Previous Secondary Receiver 

Prototype Smart Contract Transaction:
- Token Quantity Attached
- Nominated Secondary Receiver (Default Community Treasury)
- Secondary Receiver Name (Applied if SR nonexistent)
- Secondary Receiver Description (Applied if SR nonexistent)
- Vote to Increase (Boolean)
- Vote to Decrease (Boolean)

Contract Receives Transaction:
- If outside allotted timeframe (Lottery Closing Logic Loop)
- Add token attached to User Amount Spent
- Add user to Users if User not in Users
- Add Token Quantity to Total Pool
- If Secondary Receiver in Secondary Receivers
  - Add token quantity votes to Secondary Receiver Votes
- Else
  - Add Secondary Receiver to Secondary Receivers
  - Add token quantity to Secondary Receiver Votes
  - Add Name to Secondary Receiver Names
  - Add Description to Secondary Receiver Description
- Add 1 to votes to increase if vote to increase
- Add 1 to votes to decrease if vote to decrease

Lottery Closing Logic Loop:
- Generate Random number between 0 and 1
- Multiply By number of votes
- Find Address associated with vote number calculated above => Winner
- Compute Percent going to winner vs Secondary Receiver from percent difference 
between votes. Tanh? Save percent.
- Find top ranked Secondary Receiver and Save Value. Send 1 - winner percent to this address
- Send winner percent to winner
