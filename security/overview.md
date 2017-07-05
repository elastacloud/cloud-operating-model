# Securing your Cloud environment

A key part of being able to operate securely in the Cloud is understanding your business requirements. Having this understanding not only helps your choose an appropriate Cloud provider but also helps your teams build and delivery the right solutions, avoiding solutions where you just *"throw everything in"*. This last part is also crucial in terms of your operating model, knowing what data you will be storing will help you determine the levels of security to apply. For instance, you wouldn't necessarily apply the same level of control to publicly accessible data as you would to data which is subject to Data Protection laws.

Ongoing monitoring and checking of the environment plays a key role. If left to the very end of a project you will often find yourself in a situation where deadlines are missed because of re-work, or you have to "make do" with what has been delivered because your either out of time, budget or both. Ensuring that you have the capability to monitor and operate the environment you're delivering to provides you with the opportunity to identify issues early and resolve them quickly. Gaining knowledge of the system early also helps when providing early life support for your systems as your operational team have already been exposed to the solution they're supporting.

## Securing resources

Depending on your business requirements the two key areas to identify when assessing any technical component is it's ability to encrypt your data and keep your customers safe. Even if you operate only with data held in the public domain you are still likely to have customer information, personaly identifiable information or some other kind of value add data which you will want secured.

### Encryption at rest

Putting your trust into somebody else is always difficult, trusting them with yours and your customers data is often more so. One way to help alleviate this concern is to ensure that when your data is stored it is also encrypted. Cloud providers offer varying levels of support for encrypting your data, in some services this might not be available whilst in others you can bring your own key management solution. With some this is a feature you must enable whilst others have it enabled by default, using a transparent key management system managed by the provider.

If you are using infrasture services for the provisioning of virtual machines then you might want to investigate if the storage solution where the virtual drive is located can be encrypted, or if you can encrypt all or part of the drive itself.

Encrypting your data while it is at rest means that it becomes less likely that someone else, either maliciously or accidentally, can see your data in a usable form. After this it is then up to you and your organisation to determine if the simple, transparent key management solution offered by the provider is sufficient or if you need to utilise your own key management solution. Rolling your own, whilst often offers a greater level of security acceptance will almost always result in a more complex environment to manage and may introduce performance degredation to your solution. Understanding your business requirements will help to determine which solution you pursue.

### Encryption in transit

Securing your data whilst it is moving between services and between your platform and your customers is critical not only for protecting data but also to protect your customers and yourself from possible attack.

For services offering API access to data this is often a case of ensuring that access is only made over a secure HTTP connection. This may be the default but if the Cloud provider offers HTTP only access then it's worth checking to see if this can be disabled.

Other services will require further investigation and individual policies around their usage may be required. Microsoft SQL Server (or Azure SQL) for instance offers encrypted connections, in the case of Azure SQL it is the default and cannot be disabled. However developers can modify connection settings so that the validity of security certificates are not checked. In that case having a [secure development lifecycle](../development/secure-development-lifecycle.md) with a team who are knowledgable of the technical stack being utilised greatly reduces the risk of exposure.

* Managing security
  * Separation
  * Identity
  * Securing resources
  * Monitoring
* Securing the platform

## References

1. [NCSC - Understanding cloud security](https://www.ncsc.gov.uk/guidance/introduction-understanding-cloud-security)