# episerver-snippets
Episerver code snippets for cms and commerce
Contact filter by BF
```csharp
var from = customerFilter.DateFrom;
var to = customerFilter.DateTo;
var filters = new List<FilterElement>();
filters.Add(new IntervalFilterElement("Created", @from, to));
filters.Add(new OrBlockFilterElement(
     FilterElement.EqualElement("IsResign", "0"),
     FilterElement.IsNullElement("IsResign")));
if (customerFilter.IsKakaoMember)
{
    filters.Add(FilterElement.IsNotNullElement("AUID"));
    filters.Add(FilterElement.NotEqualElement("AUID", string.Empty));
}

var contacts = BusinessManager.List("Contact", filters.ToArray()).Select(c => c as CustomerContact);
```
