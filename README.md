⚠️ **Repository Archived – MedTech OSS**

`Status: Archived as of April 13, 2026`


This repository is part of the open-source assets associated with the Microsoft MedTech service. The MedTech service has been formally deprecated, and there are no remaining active customers using the service. As a result, this repository is no longer maintained and has been archived to prevent confusion for customers and the broader open-source community.

**Why this repository is being archived**

Following the deprecation of the MedTech service and the completion of customer transitions away from the platform, Microsoft has made the decision to discontinue ongoing maintenance of associated open-source repositories. Continuing to host these projects as active may create the impression of ongoing support or recommended usage, which is no longer accurate.


**Important dates**

- May 3, 2025 – Initiation of MedTech service deprecation and prevention of new instance creation
- April 13, 2026 – Archival of this open-source repository

**Acknowledgements**

We would like to sincerely thank the community of contributors, collaborators, and customers who engaged with this project over time. Your feedback, issue reports, documentation improvements, and code contributions helped shape the evolution of device data interoperability solutions within Microsoft’s healthcare ecosystem.

**What’s next?**

Microsoft continues to invest in healthcare interoperability, cloud-native data platforms, and AI-powered transformation services across Azure Health Data Services and related offerings. Future innovation in this space is being delivered through actively supported Microsoft healthcare platform capabilities.
To learn more about current Microsoft healthcare interoperability solutions, please refer to:

- [ Azure Health Data Services](https://learn.microsoft.com/en-us/azure/healthcare-apis/)
- [FHIR service in Azure Health Data Services](https://learn.microsoft.com/en-us/azure/healthcare-apis/fhir/)
- Community discussions on https://stackoverflow.com/questions/tagged/azure-health-data-services


**The original README content has been preserved below for historical reference.**

# IomtFhirClient Swift Library

[![Build Status](https://microsofthealth.visualstudio.com/Health/_apis/build/status/POET/IomtFhirClient_Daily?branchName=master)](https://microsofthealth.visualstudio.com/Health/_build/latest?definitionId=436&branchName=master)

The IomtFhirClient Swift library simplifies sending IoMT (Internet of Medical Things) data to an [IoMT FHIR Connector for Azure](https://github.com/microsoft/iomt-fhir) endpoint for persistance in a FHIR® server.

## Installation

IomtFhirClient uses **Swift Package Manager** to manage dependencies. It is recommended that you use Xcode 11 or newer to add IomtFhirClient to your project.

1. Using Xcode 11 go to File > Swift Packages > Add Package Dependency
2. Paste the project URL: https://github.com/microsoft/iomt-fhir-client
3. Click on next and select the project target

## Basic Usage

### Instantiate an IomtFhirClient

An IomtFhirClient can be instantiated using a connection string.

```swift
let iomtFhirClient = try IomtFhirClient.CreateFromConnectionString(connectionString: "YOUR_CONNECTION_STRING")
```

### Create EventData

In the example below, a simple json payload is used to create an EventData object.  

```swift
let json = "{\"eventPayload\":\"payload data\"}"

let payload = json.data(using: .utf8)

let eventData = EventData(data: payload)
```

### Send the data to the Azure Event Hub

The IomtFhirClient has methods for sending single EventHub objects or collections.

```swift
do {
    try iomtFhirClient.send(eventData: eventData) { (success, error) in
        if (success && error == nil) {
            // The event was send successfully
        } else {
            // Handle any errors
        }
    }
} catch {
    // Handle any errors
}
```

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

There are many other ways to contribute to the IomtFhirClient Project.

* [Submit bugs](https://github.com/microsoft/iomt-fhir-client/issues) and help us verify fixes as they are checked in.
* Review the [source code changes](https://github.com/microsoft/iomt-fhir-client/pulls).
* [Contribute bug fixes](CONTRIBUTING.md).

See [Contributing to IomtFhirClient](CONTRIBUTING.md) for more information.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

FHIR® is the registered trademark of HL7 and is used with the permission of HL7. Use of the FHIR trademark does not constitute endorsement of this product by HL7.
