# Dynamic Member Email — SFMC demonstration

This project uses fictional data. Review and adapt the logic in a Salesforce Marketing Cloud test environment before use.

## Example AMPscript

```ampscript
%%[
VAR @firstName, @memberType, @greeting
SET @firstName = AttributeValue("FirstName")
SET @memberType = AttributeValue("MemberType")

IF Empty(@firstName) THEN
  SET @greeting = "there"
ELSE
  SET @greeting = ProperCase(@firstName)
ENDIF
]%%

<h1>Hello %%=v(@greeting)=%%!</h1>

%%[ IF @memberType == "Gold" THEN ]%%
  <p>As a Gold member, you can explore your exclusive rewards.</p>
%%[ ELSEIF @memberType == "Silver" THEN ]%%
  <p>Thank you for being a valued member.</p>
%%[ ELSE ]%%
  <p>Discover the benefits of membership.</p>
%%[ ENDIF ]%%
```

## Suggested test cases

| FirstName | MemberType | Expected result |
|---|---|---|
| Alex | Gold | “Hello Alex!” and Gold message |
| Priya | Silver | “Hello Priya!” and Silver message |
| Empty | Standard | “Hello there!” and standard message |

## Data Extension fields

- SubscriberKey — Text, primary key
- FirstName — Text
- MemberType — Text

Do not include real customer data in a public portfolio. Use a test Data Extension and validate personalization in Preview and Test.
