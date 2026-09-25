# Finding the Right Power Automate Plan

Licensing with Power Automate is not a one-size-fits-all deal. Whether you are experimenting solo, building for an enterprise, or scaling unattended automation, Microsoft offers flexible licensing paths for different needs.

| License type | Target audience | Key features | Limitations |
|---|---|---|---|
| Free | Individuals exploring automation | Standard connectors, basic cloud flows | No premium connectors or desktop flows |
| Trial | Users testing premium features | Full access to premium features for a limited time | Expires after ~30 days |
| Premium (User license) | Professionals and teams | Unlimited cloud flows, attended RPA, premium connectors, AI Builder, Dataverse | Licensed per user |
| Process (Capacity license) | Enterprises at scale | Unattended RPA, licensed per flow/machine, backend automation | Not tied to individual users |
| Pay-as-you-go | Flexible or seasonal use | Charges based on actual usage, no upfront commitment | Cost may vary with usage |
| Add-ons | Advanced users | Hosted machines, extra AI credits, additional Dataverse storage | Requires a base license |

*Table 1.4: Key features*

## Individual Users: Automate with Freedom or Limits

- **Power Automate Premium** — The all-access pass for individual users: cloud flows, attended desktop flows, RPA, premium and custom connectors, AI features, and process mining. Well suited for users who need to automate across multiple platforms with end-to-end control.
- **Power Automate Free** — The sandbox. Standard cloud flows and local desktop automation, limited to standard connectors with no advanced features. Good for internal tasks, but does not scale beyond that.
- **Trial license (90 days)** — Nearly everything from the Premium plan, including unattended desktop flows, for a limited time. Ideal for testing the waters, building a proof-of-concept, or evaluating fit for your team.

## Organizations and Automation at Scale

Capacity-based licenses make more sense when workflows run behind the scenes or support broader business systems — they are not tied to any one person and focus on how much automation you need to run.

- **Power Automate Process** — Built for background execution. Supports cloud and desktop flows running unattended (without a user logged in). Right fit for scenarios like invoice processing, system syncs, or file routing. Includes premium connectors, custom connector support, and high daily request limits.
- **Power Automate Hosted Process** — Everything from the Process license, without the infrastructure burden — Microsoft hosts and maintains the virtual machines, so there's no need to handle provisioning, upkeep, or scaling.

## Selecting the Right License

- **Free or trial** — If you're just starting with basic flows.
- **Premium** — If you're a power user or RPA-heavy developer.
- **Process or hosted process** — If you're building scalable, unattended flows across the organization.
- **Developer plan** — For testing, demoing, or building a lab setup.

The right license depends on who is running the automation, how it runs, and how far you want to scale. Don't pick based on features alone — pick based on the kind of automation journey you are building.

For the most up-to-date licensing details, see the [Power Automate Licensing Guide](https://learn.microsoft.com/en-us/power-platform/admin/pricing-billing-skus).

## Power Automate Desktop Features in Windows 10 and 11

Windows 10 and 11 users automatically receive free PAD access, enabling RPA for automating manual tasks directly on their computer — attended desktop flows, where automation works while you're sitting at the machine.

Not included with this built-in license:
- Unattended desktop flows (running on their own without any user logged in).
- Triggering desktop flows from cloud flows.

For these advanced capabilities, you need a separate Power Automate license that supports unattended execution and cloud-to-desktop integration.

## Licensing for Cloud Flows

- **Standard connectors** — Pre-built integrations with commonly used Microsoft and third-party services (Outlook, SharePoint, Excel), available with Microsoft 365 plans.
- **Premium connectors** — Access to advanced services (Salesforce, Dataverse, SAP) beyond what's available in Microsoft 365 by default. Require a Power Automate Premium license.
- **Cloud flows that trigger desktop flows** — When a cloud-based event needs to initiate a desktop automation on a local or virtual machine. Also requires a premium license.
