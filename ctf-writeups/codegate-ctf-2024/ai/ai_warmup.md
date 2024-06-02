---
description: pyjail
---

# ai\_warmup



<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

***

## Solution

For the first part, it prompts us a CAPTCHA. Just input the right answer based on the question given and we can proceed to the next part.

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

{% code title="solve_captcha.py" lineNumbers="true" %}
```python
import hashlib
import string
import itertools

# Provided values
salt = ""
target_hash = ""
difficulty = 4  # Length of the correct string

def find_correct_str(salt, target_hash):
    characters = string.ascii_letters + string.digits
    for combo in itertools.product(characters, repeat=difficulty):
        correct_str = ''.join(combo)
        full_str = salt + correct_str
        if hashlib.sha256(full_str.encode()).hexdigest() == target_hash:
            return correct_str
    return None

cracked_str = find_correct_str(salt, target_hash)

if cracked_str:
    print(f"Cracked! The correct string is: {cracked_str}")
else:
    print("Failed to crack the CAPTCHA.")
```
{% endcode %}

For the next part, the AI Assistant will generate a code based on the user input. The catch is, there are several words/command being blocked in the source code as shown as below.

<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption><p>blacklisted keyword</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

So we cannot use commands like `ls`, `cat flag`, `grep "flag"` etc.

Instead, we send a&#x20;
