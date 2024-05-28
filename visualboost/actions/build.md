# Build

The **Build** action describes the process where the software architecture is transformed into source code and then pushed to the respective Git repositories.&#x20;

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Before a build can be performed, a commit message, a version number, and the specification of target systems are required.

* **Commit message:** Will be used for the git commit.
* **Version number:** The semantic version of the project. The version number is automatically incremented for each build. It can be manually adapted.
* **Generation Settings:** Defines whether a server application, client source code or both will be generated.
*

Clicking the **Commit** button initiates the build process:

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

After the build process successfully finished, the result will look like fhe following:

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>
