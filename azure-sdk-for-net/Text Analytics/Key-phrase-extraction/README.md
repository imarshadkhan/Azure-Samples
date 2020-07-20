# Extracting Key Phrases from text using the .netsdk
This sample demonstrates how to Extracting Key Phrases from text. 

## Prerequisites

-   Azure subscription -  [Create one for free](https://azure.microsoft.com/free/)
-   The  [Visual Studio IDE](https://visualstudio.microsoft.com/vs/)
-   Once you have your Azure subscription,  [create a Text Analytics resource](https://ms.portal.azure.com/#create/Microsoft.CognitiveServicesTextAnalytics "Create a Text Analytics resource") in the Azure portal to get your key and endpoint. After it deploys, click  **Go to resource**.
    -   You will need the key and endpoint from the resource you create to connect your application to the Text Analytics API. You'll paste your key and endpoint into the code below later in the quickstart.
    -   You can use the free pricing tier (`F0`) to try the service, and upgrade later to a paid tier for production.

## Setting up

### Create a new .NET Core application

Using the Visual Studio IDE, create a new .NET Core console app. This will create a "Hello World" project with a single C# source file:  _program.cs_.

Install the client library by right-clicking on the solution in the **Solution Explorer** and selecting **Manage NuGet Packages**. In the package manager that opens select **Browse** and search for `Azure.AI.TextAnalytics`. Select version `1.0.0`, and then **Install**. You can also use the [Package Manager Console](https://docs.microsoft.com/en-us/nuget/consume-packages/install-use-packages-powershell#find-and-install-a-package).

## Code
Open the _program.cs_ file and replace the code with following:

```
using System;
using Azure;
using System.Globalization;
using Azure.AI.TextAnalytics;
namespace ConsoleApp1 {
	class Program {
		private static readonly AzureKeyCredential credentials = new AzureKeyCredential("<Key>");
		private static readonly Uri endpoint = new Uri("<endpoint>");
		static void Main(string[] args) {
			var client = new TextAnalyticsClient(endpoint, credentials);
			// You will implement these methods later in the quickstart.

			KeyPhraseExtractionExample(client);

			Console.Write("Press any key to exit.");
			Console.ReadKey();
		}
		static void KeyPhraseExtractionExample(TextAnalyticsClient client) {
			var response = client.ExtractKeyPhrases("My cat might need to see a veterinarian.");

			// Printing key phrases
			Console.WriteLine("Key phrases:");

			foreach(string keyphrase in response.Value) {
				Console.WriteLine($ "\t{keyphrase}");
			}
		}

	}
}
```
### Output

```
Key phrases:
    cat
    veterinarian

```

##
