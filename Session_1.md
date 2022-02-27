# Session 1

These are all the examples for the quiz in the first Automated Testing LU session!

## Example 1

```javascript
function validateEmail(input) {
    const parts = input.split('@')
    return parts.length == 2 &&
        parts[0].length > 0 &&
        parts[1].length > 0
}

test('email validation fails on a wrong email', () => {
    // given
    const userInput = 'johnmiller(at)gmail.com'
    // when
    const isValidEmail = validateEmail(userInput)
    // then
    expect(isValidEmail).toBe(false)
})
```

## Example 2

```javascript
import { db } from './db'
import { validateEmail } from './validators'

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

## Example 3

```java
public class User {
    ...
    public String getName() {
        return this.name
    }
    ...
}
```
