# Session 4

These are all the examples for the quiz in the fourth Automated Testing LU session!

## Example 1

```javascript
test('BankAccount: Withdraw from Account', (account) => {
    account.setBalance(0)
    account.deposit(5)

    expect(account.withdraw(5)).equals(true)
    expect(account.withdraw(1)).equals(false)
    account.setOverdraftLimit(1)
    expect(account.withdraw(1)).equals(true)
})
```

## Example 2

```python
def test_create_user(client):
    # when
    response = client.post("/persons/create", data={
        "first_name": "John",
        "last_name": "Smith",
    })

    # then
    assert "John Smith" in response.text
    from_db = Person.find_by_last_name(last_name="Smith")
    assert from_db.first_name == "John"
    assert from_db.last_name == "Smith"


def test_list_users(client):
    # when
    response = client.get("/persons")

    # then
    assert response.text == '[{"first_name":"John","last_name":"Smith"}]'
```
    
    
## Example 3

```python
# You can assume that:
# * all functions like "get_by_role" have a built-in way of waiting
#   until the necessary element exists, and if the element doesn't exist until
#   a previously-specified timeout, the test fails.
# * The tests run using a test database with predetermined content

def test_user_can_log_in_and_change_their_username(page: Page):
    # automatically open a browser tab with this url
    page.goto("https://myawesomewebsite.com")

    # click on the first button containing "Login or Sign up"
    page.get_by_role("link", name="Log in or Sign Up").click()

    # fill the first input with label "Email"
    page.get_by_label("Email").fill("john.doe@example.org")
    page.get_by_label("Password").fill("password123")
    # click the first button containing "Login"
    page.get_by_role("button", name="Login").click()
    
    # verify that the browser shows the text "Dashboard" somewhere
    expect(page.locator("body")).to_contain_text("Dashboard")
    
    # click the first button containing "Settings"
    page.get_by_role("link", name="Settings").click()
    # verify that the browser shows the text "Username: john.doe" somewhere
    expect(page.locator("body")).to_contain_text("Username: john.doe")

    # fill input with label "Username"
    page.get_by_label("Username").fill("mynewusername")
    page.get_by_role("button", name="Save")

    # verify that the page shows "Username: mynewusername" somewhere
    expect(page.locator("body")).to_contain_text("Username: mynewusername")
```

## Example 4

```javascript
import { createMockFunction } from 'test-framework'
import { userRepository } from './userRepository'

test('User repository should save userdata to database', () => {
    // given
    const user = { name: "Anna", age: 28 }
    const saveToTableMock = createMockFunction(
        function(table, data) {
            console.log('TABLE:', table, '| data:', data)
        }
    )
    userRepository.mock({ saveToTable: saveToTableMock })
    // when
    userRepository.saveUser(user)
    // then
    expect(saveToTableMock).toHaveBeenCalledWith('users', user)
})
```
