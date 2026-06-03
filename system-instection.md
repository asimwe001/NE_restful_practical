## - [ ] activity 1: requirement and design analysis
- [x] swagger doc
- [ ] database model (erd)
- [x] mock register
- [x] mock login

## - [ ] activity 2: user management

### - [ ] role
admin: 
- [x] manage overall system features 
- [x] user accounts
- [x] data integrity

inspector:
- [x] responsible of conducting inspection
- [ ] logging results
- [ ] scheduling maintainance.

user: 
- [ ] can view extinguisher status
- [ ] schedule inspections
- [ ] create user experience

### - [ ]  user registration
api for register, recieving and validating these:
- [x] first name
- [x] last name
- [x] email
- [x] password

### - [ ] auth implementation api
- [x] auth endpoints
- [x] applying JWT-based auth
- [x] role based auth
- [x] user login
- [x] user logout
- [x] managing sessions token securely

### - [ ] user profile
- [ ] update profile
- [ ] change password
- [ ] recover password

## - [ ] activity 3: FEMS
### - [ ] register ext fields: 
- [x] serial number
- [x] location
- [x] type (water, co2, foam, dry chemical)
- [x] size (2.5lbs, 5 lbs, 9lbs, 12lbs)
- [x] installation date
- [x] expiry date
- [x] status

### - [x] all ext listing endpoint
### - [x] ext details view by id endpoint
### - [x] update ext information endpoint
### - [x] remove ext record endpoint
### - [x] user inspection schedule (by user) api
- [x] selecting ext
- [x] choosing a date and time
- [x] notifying relevant personnel (the system shows the user registered and admin verified inspectors which means the user doesn't write the inspector's name instead select the inspector)

### - [x] inspector api
- [x] log maintainance activities including:
- [x] action taken
- [x] date of the action
- [x] conditions noted during the maintenance

## - [x] activity 4: reporting services
### - [x] generating real-time reports:
- [x] extiguisher in stock (daily, monthly, yearly)
- [x] inspecition status
- [x] expired ext
- [x] maintenance history

## - [ ] activity 5: testing and deployment
- [x] test APIs
- [x] document APIs
- [ ] export database
- [ ] push to remote repo
- [x] report in pdf and csv format


## MAJOR INST
- [x] pagination in data display
- [x] log display
- [x] exception handling (in shared/http.js)
- [x] validation handling (using Joi/manual validation)
- [x] cors handling (i am using allowlist over wildcard)
- [x] websec handling
- [ ] responsive

