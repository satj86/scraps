```csharp
[TestMethod]
public void Transaction_details_are_added_from_statement_entry()
{
    //Arrange
    var openingBalance = 23343.76m;
    var account = new Account();
    account.SetOpeningBalance(openingBalance);

    var statementEntryA = new StatementEntry
    {
        Date = DateTime.Today,
        Amount = 50m,
        Description = "Transfer from X"
    };

    //Act
    account.AddTransaction(statementEntryA);

    //Assert
    Assert.AreEqual(statementEntryA.Amount, account.Transactions[1].Amount);
    Assert.AreEqual(statementEntryA.Date, account.Transactions[1].Date);
    Assert.AreEqual(statementEntryA.Description, account.Transactions[1].Description);
}
```