# Session 3

These are all the examples for the quiz in the third Automated Testing LU session.

## Example 1

--> Function with side effect

```python

```

## Example 2

--> pure fct

```python
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
