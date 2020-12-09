---
description: 'How to post stats using C# .NET.'
---

# C\#



```csharp
using System.Net.Http;
...
private static readonly HttpClient client = new HttpClient();
...
public async Task PostStats()
{
    var values = new Dictionary<string, dynamic>
    {
        { "guildCount", guildCount }
    };
    
    const string endpoint = $"https://dbots.co/api/v1/bots/{botId}/stats";

    var content = new FormUrlEncodedContent(values);
    var response = await client.PostAsync(endpoint, content);
    var responseString = await response.Content.ReadAsStringAsync();
}
```

