# MalWhere?

<figure><img src="../../../.gitbook/assets/image (69).png" alt=""><figcaption></figcaption></figure>

***

## Honourable Mention

[ad3n](https://ad3n.gitbook.io/ad3n) - for helping me and solving this challenge. Kudos!

***

## Solution

Given us a **.exe** file that is not a malwere, but Antivirus detects it as a malwere because this file using some functions that are commonly seen in a malware, says the author.

If that being said, we start our static analysis with reading the file's strings.

<figure><img src="../../../.gitbook/assets/image (70).png" alt=""><figcaption><p>there are a lot going on here, using head is better</p></figcaption></figure>

We can see a powershell script being executed upon running the executable.

We notice that are a something hiding inside the **base64 encoding**, so we develop a .py script to decode it and it looks like this.

{% code title="script.py" overflow="wrap" %}
```python
import base64
import gzip
import io

compressed_data = "H4sIAC3yPWUA/21ST+saMRT8KjlsUEkDef/yp7JQWvhBoVAvPYmHtQhaRIvY0kM/vC9bTDz0sodhMjNvZofrTzOa7ffjdNvudh+W29PlvltKIAshOYbVu39IIlREfAOIi0UsLjyBktlmCR5Kp4BFFtdFAlrJ2ckTYFRVjj49gaw2MaHn3GVBjdFDeyQqCxIcNg7KzHGITaewTYA+dk6oHHrRiaQXcPDcXlFOFkCVe8CElhg9toSQajWl30AhWsigRazWw236T5uJ2EIE13xq3hK6hLDWoL7U4mtRxNo2txqYbIbXdlHUV3JfBClboOBiU0HSEsQ32aI+qFF7kKDJArnug6XWFPpm80Q6a1NlrY0wuxYENFpCx+0cVbSS+p+RlIA6RjOJmkOEXB+5/l2RO4OK3sK61tzq+TaaWq3/cT1dzGKxHqY/Y/1zO7Afh8Pl9/vNt49fPn8yzuibyjJ/zddfd/92Oh/M/N1M96MZ9usHQYmIpvgCAAA="
decoded_data = base64.b64decode(compressed_data)
stream = io.BytesIO(decoded_data)
with gzip.GzipFile(fileobj=stream, mode='rb') as f:
   recovered_data = f.read().decode('utf-8')

print(recovered_data)
```
{% endcode %}

So we had a readable function that calculates an ASCII values and append it together.

<figure><img src="../../../.gitbook/assets/image (71).png" alt=""><figcaption></figcaption></figure>

Again, develop a script to calculate the ASCII value for variable **$op** and **$ra**.

{% code title="solve.py" overflow="wrap" %}
```python
op_values = [503%107+41, 732%105-1, 349%229+0, 984%850-19, 341%245+1, 702%588+5, 422%146-7, 832%672-48, 981%102-15, 541%150+28, 251%102+22, 894%712-68, 201%103-15, 639%240-42, 387%110+25, 472%342-27, 173%109+5, 306%181+0]
ra_values = [734%161+2, 251%90+5, 542%110+3, 802%345-14, 943%810-19, 256%158-1, 238%130+6, 823%715-3, 942%281+2, 204%103+14, 291%100+1, 422%150-6, 439%328+9, 143%72+45, 103%57+0, 743%212-4, 642%553+8, 932%164-4, 398%143-10]

op_chars = ''.join(chr(val) for val in op_values)
ra_chars = ''.join(chr(val) for val in ra_values)

print("op_chars:", op_chars)
print("ra_chars:", ra_chars)
```
{% endcode %}

So we got the strings that we wanted, turns out that variable **$op** stored our flag.

<figure><img src="../../../.gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>

***

## Flag

texsaw{p0wErSuRgE}
