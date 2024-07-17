# AI TOUR - eShop Improve Search API

## Code samples

- Initial code: `.src\00 demo\eShopLite.sln`
- Final Fixed Search code: `.\src\01 demo Search Fixed\eShopLite.sln`

## Demo Steps

- Open the solution in `.src\00 demo\eShopLite.sln`
- Run the solution
- Make a search
- Stop
- In VS2022, ask Copilot to explain the code in the solution.

  - Suggested prompt:

    ```bash
    show me the endpoints in the solution
    ```

- GH Copilot should give a general response. Focus this in the current solution using `#solution`

    ```bash
    show me the endpoints in the #solution
    ```

- Analyze the GHCopilot response and ask to explain the data class `productDataContext.cs`

    ```bash
    /explain the code in #productDataContext.cs
    ```

- (optional) ask how many sample products are added to the local test DB

    ```bash
    how many sample products are added while initializing the DB?
    ```

- Back to the SEARCH Endpoint, select the search code between the Stopwatch start/stop and ask copilot to optimize the code using Entity Framework Functions. Suggested prompt:

    ```bash
    /optimize this code, use EF Functions and like for the search. Also use the search criteria from the parameters
    ```

- The new code should look like this

    ```csharp
    List<Product> products = await db.Product
        .Where(p => EF.Functions.Like(p.Name, $"%{search}%"))
        .ToListAsync();
    ```

- Run the search again. In the test video the search process went down from 11 seconds to 0.2 seconds.

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft 
trademarks or logos is subject to and must follow 
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
