# Booking Confirmation — SFMC demonstration

A fictional transactional email concept. The fields below are illustrative; connect them to an approved data source only in a test environment.

## Suggested Data Extension fields

| Field | Type | Example |
|---|---|---|
| SubscriberKey | Text | DEMO-1001 |
| FirstName | Text | Alex |
| BookingReference | Text | DEMO-2048 |
| Destination | Text | Jaipur |
| TravelDate | Date | 2026-12-12 |

## Example AMPscript

```ampscript
%%[
VAR @firstName, @bookingRef, @destination, @travelDate
SET @firstName = AttributeValue("FirstName")
SET @bookingRef = AttributeValue("BookingReference")
SET @destination = AttributeValue("Destination")
SET @travelDate = AttributeValue("TravelDate")

IF Empty(@firstName) THEN
  SET @firstName = "traveller"
ENDIF
]%%

<h1>Your trip is confirmed, %%=v(@firstName)=%%.</h1>
<p>Booking reference: %%=v(@bookingRef)=%%</p>
<p>Destination: %%=v(@destination)=%%</p>
<p>Travel date: %%=FormatDate(@travelDate, "dd MMM yyyy")=%%</p>
```

## QA notes

- Confirm the sending context supplies the expected attributes.
- Test blank and populated values.
- Validate date formatting and time-zone assumptions.
- Check all links and tracking requirements.
- Never send this demonstration to real recipients.
