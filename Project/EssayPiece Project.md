- [ ] Authentication  username or email with password ^vcew
- [ ] User Roles Admin, SuperAdmin, Writer and Client ^mjzi
- [ ] All the users have username, email, phone number, password
- [ ] Writer's Profile has reviews, orders , success , about me, languages (array), status, profile picture, skills (array) 
- [ ] Client profile has country, orders, accepted , pay rate ,balance , phone number 
- [ ] table for skills and languages
- [ ] table for transactions with date, amount , type (deposit, withdrawal), status, description
- [ ] create patch,update ,delete and create for the orders
- [ ] add order status as open,draft or closed


EssayPiece is a essay   writing  website with api using Fastapi where Clients post essays and writers are assigned the orders . Clients do payments which load there balance and is deducted once the order task is completed. Write the code with Fast api .

###  Frontend

- [x] Fix Login UI ✅ 2024-10-31
- [x] Fix Signup UI ✅ 2024-10-31
- [x] Add login via Google UI ✅ 2024-10-31
- [ ] Login Via google api integration
- [x] Add Forgot password ✅ 2024-10-31
- [x] Change the order steps to vertical collapsible ✅ 2024-11-04
- [ ] Create Order
- [ ] Update backend Models for Order
- [ ] Add Pricing
- [ ] List wiriters
- [ ] Admin


### Shadcn extensions

https://shadcnui-expansions.typeart.cc/
https://shadcn-extension.vercel.app/
https://enhanced-button.vercel.app/

{
  "product": 45,
  "deadline": "2024-11-04T14:00:00.554Z",
  "for_final_date": null,
  "language": 2,
  "level": 4,
  "service": 2,
  "quantity": 1,
  "space": 1,
  "words_count": 275,
  "size_type": "Words",
  "topic": "Comunnicationnwith LLM",
  "description": "Education with LLM Study<br>",
  "price": null,
  "subject": "Education",
  "number_of_sources": 3,
  "style": 3,
  "is_private": false,
  "promocode": null,
  "client_id": "pgnfidgwuKhlfrh4jRuIirRpvteChDGnga9I4hmj"
}

Admin
Create admin Dashboard section where admin can view
Total Balance Deposited,
Total Withdrawal,
Total Refunds,

 - Number of clients
 - Number of writers
 - Number of orders
 Number of 
Orders in Progress,
Orders Rejected,
Orders Pending,
Orders  Done



Clients list with top orders with number of orders,
Top Writers list online,

List of top Subjects with number of orders

Also Add any other statistic that may be needed in the admin dashboard

link sample
https://www.youtube.com/watch?v=eLtmSLdrREM
https://microelephant.io/demo/prowriters/admin/tasks

Add Transaction sidebar link with the following sub links:
Received Payments - This has all the payments done with  id, Date , From , Method (Stripe, Bank Deposit, Cash) with Reference number and Amount

Pending Payment Approvals - like Received payments but with Actions for Approve and Disapprove

Wallet Transactions - This has all the wallet transactions done with  Id, Date , User, Description and Amount


