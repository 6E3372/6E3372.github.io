# Pa+rio+ik

***

<figure><img src="../../../../.gitbook/assets/image (10) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## Penyelesaian

Diberi file `ELF 64-bit` bernama chall yang meminta kita memasukkan flag.

<figure><img src="../../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Analisa file tersebut menggunakan ghidra, kita mendapati bahawa bendera tersebut diencrypt di fungsi [#encrypt](pa+rio+ik.md#encrypt "mention") lalu dibandingkan dengan bendera sebenar yang telah diencrypt pada [#main](pa+rio+ik.md#main "mention") program.

Salah satu cara menyelesaikan tugasan ini adalah dengan dekod semula bendera sebenar.

Satu cara lagi adalah dengan bruteforce. Saya sedar bahawa apabila kita memasukkan format bendera yang bermula dengan `3108{`, program tersebut mengucapkan terima kasih, bermaksud bendera kita adalah betul

<figure><img src="../../../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Maka, saya bruteforce program tersebut secara manual menggunakan deskripsi yang diberikan pada soalan iaitu "Bangsa" sehingga mendapatkan bendera yang sebenar 😄

<figure><img src="../../../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## Bendera

3108{B4NG5A\_M3RD3K4}

***

### encrypt()

{% code lineNumbers="true" fullWidth="true" %}
```c
void encrypt(char *__block,int __edflag)

{
  long lVar1;
  byte abStack_c8 [8];
  char *local_c0;
  int local_b8 [4];
  undefined4 local_a8;
  undefined4 local_a4;
  undefined4 local_a0;
  undefined4 local_9c;
  undefined4 local_98;
  undefined4 local_94;
  undefined4 local_90;
  undefined4 local_8c;
  undefined4 local_88;
  undefined4 local_84;
  undefined4 local_80;
  undefined4 local_7c;
  undefined4 local_78;
  undefined4 local_74;
  undefined4 local_70;
  undefined4 local_6c;
  undefined *local_60;
  long local_58;
  size_t local_50;
  ulong local_48;
  int local_3c;
  
  local_c0 = __block;
  local_50 = strlen(__block);
  local_58 = local_50 - 1;
  lVar1 = ((local_50 + 0xf) / 0x10) * -0x10;
  local_60 = abStack_c8 + lVar1;
  local_b8[0] = 2;
  local_b8[1] = 0;
  local_b8[2] = 1;
  local_b8[3] = 9;
  local_a8 = 0x4a;
  local_a4 = 0x7b;
  local_a0 = 5;
  local_9c = 0x67;
  local_98 = 0x7e;
  local_94 = 4;
  local_90 = 0x78;
  local_8c = 0x6e;
  local_88 = 100;
  local_84 = 2;
  local_80 = 0x6b;
  local_7c = 0x7d;
  local_78 = 2;
  local_74 = 0x62;
  local_70 = 5;
  local_6c = 0x4c;
  for (local_3c = 0; (ulong)(long)local_3c < local_50; local_3c = local_3c + 1) {
    if ((local_c0[local_3c] < 'A') || ('Z' < local_c0[local_3c])) {
      if (('`' < local_c0[local_3c]) && (local_c0[local_3c] < '{')) {
        local_c0[local_3c] =
             (char)(local_c0[local_3c] + -0x59) +
             (char)((local_c0[local_3c] + -0x59) / 0x1a) * -0x1a + 'a';
      }
    }
    else {
      local_c0[local_3c] =
           (char)(local_c0[local_3c] + -0x39) + (char)((local_c0[local_3c] + -0x39) / 0x1a) * -0x1a
           + 'A';
    }
  }
  for (local_48 = 0;
      (local_48 < local_50 &&
      (abStack_c8[local_48 + lVar1] = local_c0[local_48] ^ 0x31,
      (int)(char)abStack_c8[local_48 + lVar1] == local_b8[local_48])); local_48 = local_48 + 1) {
  }
  return;
}
```
{% endcode %}

### main()

{% code lineNumbers="true" %}
```c
undefined8 main(void)

{
  char extraout_AL;
  size_t sVar1;
  int __edflag;
  undefined8 uStack_30;
  char local_28 [32];
  
  uStack_30 = 0x10144e;
  printf("Masukkan flag: ");
  __edflag = 0x19;
  uStack_30 = 0x101466;
  fgets(local_28,0x19,stdin);
  uStack_30 = 0x101472;
  sVar1 = strlen(local_28);
  if (local_28[sVar1 - 1] == '\n') {
    uStack_30 = 0x10148b;
    sVar1 = strlen(local_28);
    local_28[sVar1 - 1] = '\0';
  }
  uStack_30 = 0x1014a0;
  encrypt(local_28,__edflag);
  if (extraout_AL == '\0') {
    uStack_30 = 0x1014c4;
    puts("Anda kurang semangat patriotisme");
  }
  else {
    uStack_30 = 0x1014b3;
    puts("Terima kasih kerana menjadi rakyat yang menghargai sejarah negara");
  }
  return 0;
}
```
{% endcode %}
