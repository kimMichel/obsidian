It's common for software projects to depend on external packages or dependencies. Managing these external dependencies consumes resources and affects productivity. These dependencies can also include vulnerabilities that introduce security threats. A vulnerability is a flaw in a project's code that can be exploited. These exploits can damage the confidentiality, integrity, or availability of the project or other projects that use it s code. You might not even notice dependency vulnerabilities right away, because they exist outside of the code on which you work. Understanding how to effectively and efficiently manage your dependencies with Github improves the security of your software supply chain.

# The Dependency graph

![[Pasted image 20251201101859.png]]

The dependency graph is a summary of the manifest and lock files stored in a repository and any dependencies that are submitted for the repository using the Dependency submission API. These files contain metadata about your project. The dependency graph is automatically generated of public repositories and includes the following information:

- Dependencies, which are the ecosystem and packages on which the repository depends.
- Dependents, which are the repositories and package that depend on the repository.

The dependency graph uses the information form your lock and manifest files to provide a list of two kinds of dependencies:

- The direct dependencies explicitly defined in a manifest or lock file or submitted with the Dependency submission API.
- The indirect dependencies, also known as transitive dependencies or subdependencies, which are dependencies used by packages that are dependencies of your project.

Lock files (or their equivalent) generate the most reliable dependency graph, because they define exactly which versions of the direct and indirect dependencies you currently use. By using lock files, you ensure that all contributors to the repository are using the same versions, making it easier for you to test and debug code. If your ecosystem doesn't have lock files, you can use premade actions that resolve transitive dependencies for many ecosystems.

# Enable the dependency graph for private repositories

As a repository administrator, you can also choose to enable the dependency graph for private repositories by completing these steps:

1. Go to your Github repository.
2. Select your repository Settings.
3. On the left-hand menu under Security, select Advanced Security.
4. In the Dependency graph section, select Enable.

```
Dependent information isn't included for private repositories.
```

# View the dependency graph

You can view the dependency graph for your repository by following these steps:

1. Go to your Github repository
2. Select your repository Insights.
3. Select Dependency graph.
4. You can select the Dependencies or Dependents tab from the Dependency graph view.

![[Pasted image 20251201104449.png]]

# Supported package ecosystem for the dependency graph

This table lists the recommended and supported formats for files containing your dependencies. If you use these formats, your dependency graph is more accurate. Using the recommended file format means that your dependency graph reflects the current build setup and can report vulnerabilities for bot direct and indirect dependencies.

We generally recommend lock files in your repository, because they define the exact versions of the direct and indirect dependencies that you're currently using. If you're using lock files, make sure the contributors to your repository are also using the same versions. If you use a manifest file (or equivalent), indirect dependencies aren't included in checks for vulnerable dependencies.

![[Pasted image 20251201104836.png]]

# The Github Advisory Database

![[Pasted image 20251201104946.png]]

The Github Advisory Database is a security vulnerability database inclusive of Common Vulnerabilities and Exposure (CVE)s and Github originated security advisories from the world of open source software. Github collects information on vulnerabilities and includes it in the Github Advisory Database to:

- Provide a free and open-source repository of security advisories.
- Enable the community to crowd-source their knowledge about these advisories.
- Surface vulnerabilities in an industry-accepted formatting standards for machine interoperability.

The Github Advisory Database contains detailed information about each vulnerability including description, severity, and affected package. This database uses the Common Vulnerability Scoring System (CVSS), Section 5 to assign a severity level to each vulnerability: low, medium/moderate, high, and critical. The database is populated from the following sources:

- Security advisories reported on Github
- The National Vulnerability Database
- The npm Security advisories database
- The FriendsOfPHP database
- The  Go Vulncheck database
- The Python Packaging Advisory database
- The Ruby Advisory database
- The RustSec Advisory database
- Community contributions
- A combination of machine learning and human reviews to detect vulnerabilities in public commits on Github.

# Software Bill of Materials (SBOM)

A Software Bill of Materials (SBOM) is a formal, machine-readable inventory of a project's dependencies and associated information (such as versions, package, and licenses). SBOMs help reduce supply chain risks by:

- Providing transparency about the dependencies used by your repository.
- Allowing vulnerabilities to be identified early in the process.
- Providing insights into the license compliance, security, or quality issues that might exist in your codebase.
- Enabling you to better comply with various data protection standards.

Github offers two ways to export a Software Bill of Materials (SBOM) for your repository. You can export the current state of the dependency graph for your repository as an SBOM using the industry-standard Software Package Data Exchange (SPDX) format:

- Through the Github UI.
- By using the REST API.

You can use SBOMs as part of your audit process and use them to comply with regulatory and legal requirements. If your company provides software to the US federal government, per Executive Order 14028, you need to provide an SBOM for your product.

# Dependabot

Dependabot is a Github tool that automates managing your repository's dependencies. Dependabot keeps your dependencies up to date by informing you of any security vulnerabilities in your dependencies. When a Dependabot alert is triggered, it automatically opens pull requests to upgrade your dependencies to the next available secure version, or to the latest version when a release is published. For Dependabot to work, the dependency graph must be enabled in a repository. Dependabot uses the dependency graph and the Github Advisory Database to provide three features:

- Dependabot alerts: These alerts notify you about vulnerable dependencies. Including, a link to the affected file in the project and information about a fixed version.
- Security updates: Automatically update or generate a pull request that updates vulnerable dependencies.
- Version updates: Automatically update supported packages used by your repository on a schedule you configure.

# Dependency review

You can use dependency review to catch vulnerable dependencies before they're added to your main branch. Dependency review helps you understand dependency changes and the security impact of these changes at every pull request. It provides an easily understandable visualization of dependency changes with a rich diff on a pull request's File Changed tab. By checking the dependency reviews in a pull request and changing any dependencies that are flagged as vulnerable, you can avoid vulnerabilities being added to your project. Dependency review informs you of:

- The dependencies that were added, removed or updated, along with the release dates.
- The number of projects that use these components.
- The vulnerability data for these dependencies.

Where Dependabot is more about automatically monitoring and updating known dependencies, dependency review proactively analyzes dependency changes during pull request to highlight key information, like insecure dependencies, enabling you to keep your project safer. Together, these complementary tools can be used to maintain a more secure and up-to-date codebase.