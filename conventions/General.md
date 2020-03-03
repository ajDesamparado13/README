# General Software Development Conventions

Table of Contents

- [Functions](#functions)
- [Condition Blocks](#condition-blocks)
  - [if statements](#if-statements)
  - [switch statements](#switch-statements)
- [Class](#class)
- [Boolean Naming](#boolean-naming)

## Functions<a name="functions"></a>

#TODO!!

## Condition Blocks<a name="condition-blocks"></a>

#### If Statements<a name="if-statements"></a>

use more if(this and that){return}, instead of nested if

Good:

    func easyReadableFunc() {
    ​
        if(!$user) {
            return;
        }
    ​
        if(!$user->hasFriends()) {
            return;
        }
    ​
        foreach($user->friends() as $friend) {
            $friend->poke();
        }
    }

Bad:

    func hardReadableFunc() {
    ​
        if($user) {
            if($user->hasFriends()) {
                foreach($user->friends() as $friend) {
                    $friend->poke()
                }
            }
        }
    }

#### Switch Statements<a name="switch-statements"></a>

## Boolean Naming<a name="boolean-naming"></a>

It is difficult to make a rule on boolean naming as case scenario differs in every situation/processes. but the important thing is to keep it simple and consistent. so I suppose what would be given here are tips to keep it simple and consistent.

Boolean Naming or even Boolean getters should be an `affirmative statements` that evaluates to either true or false

### **Boolean that verifies that every case is true**

    const XXX = users.every(user => user.isActive)

`XXX` will only be true if every user is active. How could we name the variable?

<table>
<thead>
<th>Variable</th>
<th>Any good?</th>
<th>Reason</th>
</thead>
<tbody>
<tr>
<td>isUsersLoggedIn </td>
<td>#TODO!!</td>
<td>Grammatically incorrect</td>
</tr>
<tr>
<td>areUsersLoggedIn </td>
<td>#TODO!!</td>
<td>#TODO!!</td>

<tr>
<td>isEveryUserLoggedIn </td>
<td>Okay</td>
<td>Fits with Array.prototype.every</td>
</tr>

<tr>
<td>isEachUserLoggedIn </td>
<td>Okay</td>
<td>Comes off more natural than "every" (depends)</td>
</tr>

</tbody>
</table>

### **Boolean that verifies that one of many cases is true**

    const XXX = users.some(user => user.isActive)

`XXX` will only be true if at least one user is active.

<table>
<thead>
<th>Variable</th>
<th>Any good?</th>
<th>Reason</th>
</thead>
<tbody>
<tr>
<td>isUsersActive </td>
<td>#TODO!!</td>
<td>Grammatically incorrect & ambiguous</td>
</tr>
<tr>
<td>isAtLeastOneUserActive </td>
<td>terrible</td>
<td>Too wordy</td>

<tr>
<td>isOneUserActive </td>
<td>terrible</td>
<td>Lie. This could imply that there is only one user active. Avoid confusion!!!</td>
</tr>

<tr>
<td>isSomeUserActive </td>
<td>Okay</td>
<td>Fits with Array.prototype.some</td>
</tr>

<tr>
<td>isAnyUserActive </td>
<td>Okay</td>
<td>Comes off more natural than "some" (depends)</td>
</tr>

</tbody>
</table>

### **Avoid custom prefixes**

<table>
<thead>
<th>Variable</th>
<th>Any good?</th>
<th>Reason</th>
</thead>
<tbody>
<tr>
<td>wasPaidFor </td>
<td>Okay</td>
<td>Custom prefix</td>
</tr>

<tr>
<td>paidFor </td>
<td>Terrible</td>
<td>No prefix</td>
</tr>

<tr>
<td>areBillsPaidFor </td>
<td>kinda</td>
<td>Custom Prefix</td>
</tr>

<tr>
<td>hadHaveHadBeenPaidFor </td>
<td>WTF</td>
<td>LONG Custom Prefix</td>
</tr>

<tr>
<td>isPaidFor </td>
<td>Alright!</td>
<td> simple and concise</td>
</tr>
</tbody>
</table>
 
### **Affirmative naming**

<table>
<thead>
<th>Variable</th>
<th>Any good?</th>
<th>Reason</th>
</thead>
<tbody>
<tr>
<td>isDisabled / isEmpty</td>
<td>Kinda</td>
<td>Negative</td>
</tr>
<tr>
<td>isNotActive</td>
<td>nope</td>
<td>Just Imagine if(!isNotActive){this and that}</td>
</tr>
<tr>
<td>hasNoBillingAddress</td>
<td>terrible</td>
<td>There is No need for "No"</td>
</tr>
<tr>
<td>isEnabled / isActive / hasBillingAddress</td>
<td>Alright!</td>
<td>and use it like this !isActive to get the negative</td>
</tr>
</tbody>
</table>

reference: [tips-on-naming-boolean-variables](https://dev.to/michi/tips-on-naming-boolean-variables-cleaner-code-35ig)

## Class<a name="class"></a>

#TODO!!

## ORM usage

#TODO!!

## Branch Naming<a name="branch-naming"></a>

#TODO!!

## Commit Messaging<a name="commit-messaging"></a>

#TODO!!
