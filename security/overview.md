# Securing your Cloud environment

A key part of being able to operate securely in the Cloud is understanding your business requirements. Having this understanding not only helps your choose an appropriate Cloud provider but also helps your teams build and delivery the right solutions, avoiding solutions where you just *"throw everything in"*. This last part is also crucial in terms of your operating model, knowing what data you will be storing will help you determine the levels of security to apply. For instance, you wouldn't necessarily apply the same level of control to publicly accessible data as you would to data which is subject to Data Protection laws.

Ongoing monitoring and checking of the environment plays a key role. If left to the very end of a project you will often find yourself in a situation where deadlines are missed because of re-work, or you have to "make do" with what has been delivered because your either out of time, budget or both. Ensuring that you have the capability to monitor and operate the environment you're delivering to provides you with the opportunity to identify issues early and resolve them quickly. Gaining knowledge of the system early also helps when providing early life support for your systems as your operational team have already been exposed to the solution they're supporting.

## Securing resources

Depending on your business requirements the two key areas to identify when assessing any technical component is it's ability to encrypt your data and keep your customers safe. Even if you operate only with data held in the public domain you are still likely to have customer information, personaly identifiable information or some other kind of value add data which you will want secured.

A key resource to secure is the client device which is being used to connect to Cloud resources, a compromised end-point could, at best, expose an unpriviledged user account. At worst it could expose one or more priviledged user accounts along with connection information for your Cloud resources.

### Encryption at rest

Putting your trust into somebody else is always difficult, trusting them with yours and your customers data is often more so. One way to help alleviate this concern is to ensure that when your data is stored it is also encrypted. Cloud providers offer varying levels of support for encrypting your data, in some services this might not be available whilst in others you can bring your own key management solution. With some this is a feature you must enable whilst others have it enabled by default, using a transparent key management system managed by the provider.

If you are using infrasture services for the provisioning of virtual machines then you might want to investigate if the storage solution where the virtual drive is located can be encrypted, or if you can encrypt all or part of the drive itself.

Encrypting your data while it is at rest means that it becomes less likely that someone else, either maliciously or accidentally, can see your data in a usable form. After this it is then up to you and your organisation to determine if the simple, transparent key management solution offered by the provider is sufficient or if you need to utilise your own key management solution. Rolling your own, whilst often offers a greater level of security acceptance will almost always result in a more complex environment to manage and may introduce performance degredation to your solution. Understanding your business requirements will help to determine which solution you pursue.

### Encryption in transit

Securing your data whilst it is moving between services and between your platform and your customers is critical not only for protecting data but also to protect your customers and yourself from possible attack.

For services offering API access to data this is often a case of ensuring that access is only made over a secure HTTP connection. This may be the default but if the Cloud provider offers HTTP only access then it's worth checking to see if this can be disabled.

Other services will require further investigation and individual policies around their usage may be required. Microsoft SQL Server (or Azure SQL) for instance offers encrypted connections, in the case of Azure SQL it is the default and cannot be disabled. However developers can modify connection settings so that the validity of security certificates are not checked. In that case having a [secure development lifecycle](../development/secure-development-lifecycle.md) with a team who are knowledgable of the technical stack being utilised greatly reduces the risk of exposure.

## Identity

While keeping your data secure whilst it's at rest and in transit it is also key to know who is accessing it and your systems. Managing the identity of your users plays as much of a crucial role in the Cloud as it does on-premise, allowing you to limit access to data and services to those who are authenticated and authorised to do so.

User access is typically through the use of usernames and passwords which are susceptible to compromise through phishing or malware. As with any other service credentials should be managed according to a policy which should include password strength and password rotation. Credentials should not be entered over an unsecure connection or from an end-point which is unmanaged, public or potentially compromised.

Where possible multi-factor authentication should be applied to user accounts to reduce the risk of data loss should a users credentials become compromised. The multi-factor authentication solution used should provide an 'out-of-band' solution, that is a solution which does not use the same communication channal as the one used to enter the users credentials (e.g. push notifications, authentication apps).

### Federation

Having service specific user accounts is often desirable - where a complete separation of environments is required - or unavoidable where in-service accounts are required for creation and administration. You may wish though to federate with your existing identity provider. This provides the benefit of managing a single store of identities which should already adhere to your corporate policy. In the event of an account being detected as compromised it may be easier to block access to the account from a single provider.

It is worth keeping in mind however that a federated solution may also increase the surface of any attack as all services which were protected by that identity may be open to the attacker.

### Role based access control (RBAC)

When defining your solution having an understanding of the roles required is essential to being able to secure your data and services. A full picture of all roles may not be possible at the very start but having some well defined roles gives you a position to start from. If you do start from an incomplete view then you should ensure that the roles you start with are defined and well understood and not broad roles to be broken down later, breaking roles apart at a later date becomes more complex as users have built their own processes around the roles which were defined.

There are often multiple areas where roles can be deployed, for example, developing a custom application which is to be deployed into a Cloud provider may have the following areas:

* *Cloud provider* - This is a collection of roles which will allow users to perform various tasks with the provider, such as provisioning services, managing identities or reviewing the security of the environment.
* *Service* - Within a deployed service there may be additional roles. A database service may have roles for people who can administer the database and those who can read or write data.
* *Application* - The application being developed may provide users with different roles itself such as users and administrators of the application.

If in doubt of which permissions should be applied to a role then start from a position of least priviledge and gradually add additional permissions if needed. Adding permissions gradually is always much easier than trying to take permissions away.

Separating your roles allows you to also separate the services you are consuming, reducing the impact of any compromise but also helping to protect from accidental changes. If, for example, your solution consists of a database and a web application then you would not want your database administrators to be able to tweak the configuration of your web application hosting service.

## Operational security

From the outset your service should be operated and managed securely so as to ensure that solutions are developed in a secure manner and that attacks are impeded, detected and (hopefully) prevented. Those who are operating the security of the environment should work with development teams to ensure that operational security is thought about throughout the application development lifecycle.

Importantly, as much as possible should be automated and managed through tooling with the team having all the available resource it needs itself to carry out operations. A good [operational security](../operations/operational-security.md) model should not introduce complex or heavyweight processes, or require time consuming and expensive processes. The model should allow for the rapid response and resolution of incidents.

## References

1. [NCSC - Understanding cloud security](https://www.ncsc.gov.uk/guidance/introduction-understanding-cloud-security)