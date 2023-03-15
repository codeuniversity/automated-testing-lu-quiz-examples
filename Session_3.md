# Session 3

These are all the examples for the quiz in the third Automated Testing LU session.

## Example 1

```python
def get_user_name_from_user_array(user):
   user_name = user['data']['name']
   first_name = user_name['first']
   last_name = user_name['last']
   logging.info('Name: ' + first_name + ' ' + last_name)
   if first_name and last_name:
       return first_name + ' ' + last_name
   else:
       if first_name:
           return first_name
       elif last_name:
           return last_name
       else:
           return ''
```

## Example 2

```python
# Returns index of x in arr if present, else -1
# Parameters:
#   arr: Sorted array
#   low, high: upper and lower bounds
def binary_search(arr, low, high, x):
    if high >= low:
        mid = (high + low) // 2
        if arr[mid] == x:
            return mid
        elif arr[mid] > x:
            return binary_search(arr, low, mid - 1, x)
        else:
            return binary_search(arr, mid + 1, high, x)
    else:
        return -1
```

## Example 3

```python
def nextMinuteFromNow():
    '''
    Return a date object representing the start of the next minute from now
    '''
    nowAsMillis = currentTimeInMilliseconds()
    then = Date(nowAsMillis + 60000)
    then.setSeconds(0)
    then.setMilliseconds(0)
    return then
```

## Example 4

```python
import { db } from './db'
import { saltAndHash } from './security'

function createUser(email, password) {
    const preliminaryUsername = email.split('@')[0]
    return db.createUser({
        name: preliminaryUsername,
        password: saltAndHash(password),
    })
}

test('createUser should extract the username from the email', () => {
    // given
    const expectedUsername = 'john'
    const enteredEmail = expectedUsername + '@example.com'
    const enteredPassword = 'password123'
    // when
    const createdUser = createUser(enteredEmail, enteredPassword)
    // then
    expect(createdUser.name).toBe(expectedUsername)
})
```
