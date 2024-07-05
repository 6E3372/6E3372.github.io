# Terms of Use

<figure><img src="../../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

***

### Solution

Upon unzipping the **Malware.zip**, we will be provided a microsoft word file.

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

From here, my guess is the author inject a macro code inside it.

Tools like olevba are capable of extracting the macro code inside a malicious document

Run command `olevba <filename>` and we should retrieve a flag

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

***

### Flag

grodno{MS\_0ffice\_macros\_are\_a\_source\_of\_malicious\_code.\_B3\_careful\_with\_the\_functionality\_in\_active\_MS\_0ffice\_documents}
