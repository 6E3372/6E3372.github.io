# Lemah

***

<figure><img src="../../../../.gitbook/assets/image (10) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## Penyelesaian

Mari kita lihat apa yang ada pada website tersebut

<figure><img src="../../../../.gitbook/assets/image (11) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Wow ianya adalah "Login Page" yang biasa kita lihat.

`robots.txt` tidak memberikan apa-apa.

Mari kita lihat di sources, mungkin ada yang menarik di situ?

<figure><img src="../../../../.gitbook/assets/image (12) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Betul tekaan saya. Diberi `auth.js` adalah satu code javascript kepada login page tersebut.

Kita dapat lihat pada baris ke 5 yang mengandungi if statement dengan parameter&#x20;

```
u === "Jati" 
```

dan

```
p===String.fromCharCode(51,49,48,56,123,112,52,115,115,119,48,114,100,95,108,51,109,52,104,33,125)
```

Baris ke 4 sudah mengatakan bahawa `u` adalah username dan `p` adalah password

Kita dapat lihat bahawa password adalah dalam decimal number, jadi tukarkan sahaja nombor tersebut kepada ascii.

{% code title="solve.py" lineNumbers="true" %}
```python
number = [51,49,48,56,123,112,52,115,115,119,48,114,100,95,108,51,109,52,104,33,125]

ascii = ''.join([chr(num) for num in number])

print(ascii)
```
{% endcode %}

<figure><img src="../../../../.gitbook/assets/image (13) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Oh, passwordnya adalah bendera kita! Terbaik 👍

***

## Bendera

3108{p4ssw0rd\_l3m4h!}
