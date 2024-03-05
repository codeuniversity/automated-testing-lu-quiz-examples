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
