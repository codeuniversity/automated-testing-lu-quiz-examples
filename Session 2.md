# Session 2

These are all the examples for the quiz in the second Automated Testing LU session!

## Example 1

```javascript
test('user can log in and change their username', (I) => {
    // automatically open a browser tab with this url
    I.amOnPage('https://myawesomewebsite.com/')

    // automatically click on the first button containing “Login or Sign up”
    I.click('Login or Sign up')
    // fill the first input with label “Email”
    I.fillField('Email', 'john.doe@example.org')
    I.fillField('Password', 'password123')
    // click the first button containing “Login”
    I.click('Login')

    // verify that the browser shows the text “Dashboard” somewhere
    I.shouldSee('Dashboard')

    // click the first button containing “Settings”
    I.click('Settings')

    // verify that the browser shows the text “Username: john.doe” somewhere
    I.shouldSee('Username: john.doe')

    // fill input with label “Username”
    I.fillField('Username', 'mynewusername')
    I.click('Save')

    // verify that the page shows “Username: mynewusername” somewhere
    I.shouldSee('Username: mynewusername')
})
```

## Example 2

```javascript
import { testFramework } from 'test-framework'
import { userRepository } from './userRepository'
import { db } from './db'

test('User repository should save userdata to database', () => {
    // given
    const user = { name: "Anna", age: 28 }
    const saveToTableMock = testFramework.createMockFunction(
        function(table, data) {
            console.log('TABLE:', table, '| data:', data)
        }
    )
    userRepository.mock(db, { saveToTable: saveToTableMock })
    // when
    userRepository.saveUser(user)
    // then
    expect(saveToTableMock).toHaveBeenCalledWith('users', user)
})
```
