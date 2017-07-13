# Style Guide For Database Entires

**_Warning: this document is currently not of the highest priority to the project, and therefore may be out of date, incomplete, or both_**

## People

This collection contains data about politicians

### Fields
- [name](#name)
- [party](#party)
- [link](#link)
- [state](#state)
- [district](#district)
- [position](#position)
- [donations](#donations)
- [votes](#votes)
- [\_id](#_id)

#### Name
- Must be an Object containing the person's full legal name, no nicknames, split into first, middle, and last.
- Middle name is optional. If omitted, the type should be `null`
- Must be capitalized

Example: 

    {
       first: "John",
       middle: "Hardy",
       last: "Isakson"
    }

#### Party
- Must be a String containng the name of the political party the person belongs to
- Must be capitalized and fully written out, no abreviations

Example: Republican

#### Link
- Must be a String
- Should contain the link to the person's official government homepage.
- If no government page is available, a personal one may be used.

Example: https://www.sanders.senate.gov/

#### State
- Must be a String containing the abreviation for the state the person currently represents
- Must be all uppercase

Example: GA

#### District
- Must be a 32bit Integer (int32) representing the district the person currently represents
- If the person currently represents the entire state, that integer is 0

Example: 14

#### Position
- Must be a String containing the office currently held by the person, prefixed by the jurisdiction of the governing body.
- If the jurisdiction is State, do not include the name of the state.
- Must be capitalized and not abreviated.

Example: United States House Of Representitives
Example: State Governer

#### Donations
- Must be an Object containing at least `total: 0`
- Every other key should be the [name of an issue](https://github.com/dospunk/politinfluence/blob/master/issues.md) and should represent another Object containing at least `{ pro: 0, anti: 0 }`

Example: 

    {
       total: 5000,
       'Big Business': {
         pro: 500,
         anti: 1060
       },
       'Public Education': {
         pro: 1800,
         anti: 40
       }
    }

#### Votes
- Must be an Object containing
    - The ObjectId of the bill in question with the key 'bill'
    - A String containing the person's vote ('y' or 'n') with they key 'yn'
        - The 'y' or 'n' must be lowercase

Example:

    {
       bill: ObjectId("123a456bcdefg7890h12345i"),
       yn: 'y'
    }

#### \_id
- Must be an ObjectID
- Assigned by MongoDB
- **DO NOT CHANGE THIS UNDER ANY CIRCUMSTANCES.**

Example: ObjectId("591a259ddbcdf7492c67139a")

## Entities

This collection contains data about companies, PACs, etc.

### Fields
- [name](#name-1)
- [link](#link-1)
- [issues](#issues)
- [\_id](#_id-1)

#### Name
- Must be a String containing the name of the company/PAC/etc.
- Including the type of company (ie. Bas Group vs Bas Group, LLC) is optional
- Must be capitalized

Example: Bas Group, LLC

#### Link
- Must be a String containing a link the entity's official website
- If (and only if) no website is available, a link to a Facebook page or other social media is acceptable.
- If no website or social media is available, the value should be `null`

Example: http://www.target.com/

#### Issues
- Must be an Object where the keys are names of relevant [issues](https://github.com/dospunk/politinfluence/blob/master/issues.md) and the values are Objects containing the entity's position on the issue and evidence of that position
    - The values must be [`pro`, `ppro`, `anti`, or `panti`](https://github.com/dospunk/politinfluence/blob/master/issues.md#pro-ppro-anti-and-panti) and must be all lowercase
    - If the evidence is a link, it should be formatted as an HTML <a> tag. 

Example:

    {
       'Big Business': {
          pos: "anti",
          res: "<a href="[link to statement from entity]">click here</a>"
       },
       'Environment': {
          pos: "ppro",
          res: "entity sources materials from sustainable providers"
       }
    }

#### \_id
- Must be an ObjectID
- Assigned by MongoDB
- **DO NOT CHANGE THIS UNDER ANY CIRCUMSTANCES.**

Example: ObjectId("591a259ddbcdf7492c67139a")

## Donations
### Fields
- amount
- date
- to
- from
- \_id

#### Amount

#### Date

#### To

#### From

#### \_id
- Must be an ObjectID
- Assigned by MongoDB
- **DO NOT CHANGE THIS UNDER ANY CIRCUMSTANCES.**

Example: ObjectId("591a259ddbcdf7492c67139a")

## Bills
### Fields
- name
- date
- desc
- issues
- \_id

#### name

#### date

#### desc

#### issues

#### \_id
- Must be an ObjectID
- Assigned by MongoDB
- **DO NOT CHANGE THIS UNDER ANY CIRCUMSTANCES.**

Example: ObjectId("591a259ddbcdf7492c67139a")
