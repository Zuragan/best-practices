# Apa Itu Tag?

Tag digunakan untuk menandai salah satu `commit` di repository. Tag biasanya digunakan untuk menandai apabila:

* Aplikasi siap untuk di release
* Ada hotfix di versi aplikasi yang sudah di release

Tag bersifat unik dalam satu repository, jadi kita dapat melakukan tag di branch manapun (tidak harus di branch master) dan sistem git tetap dapat me-referensi ke tag tersebut.

Referensi lebih lanjut dapat dilihat di [sini](https://git-scm.com/book/en/v2/Git-Basics-Tagging).

# Release Tag

* Ketika aplikasi siap untuk di-release dan akan diberi nomor versi `v0.1`, maka commit yang siap di-release dapat ditandai dengan perintah

```sh
~$ git tag -a v0.1
```

* Berikan keterangan release untuk tag tersebut (editor akan muncul secara otomatis)
* Tag tersebut baru akan tertulis di repo lokal, untuk menyimpannya di remote server harus dilakukan

```sh
~$ git push origin --tags
```

# Hotfix Tag

Hotfix adalah bugfix di mana perubahan yang dilakukan harus segera dimasukkan ke production (tidak bisa menunggu next feature release).

## Buat branch hotfix

Ketika harus dilakukan hotfix maka harus dilakukan branching dengan basis diambil dari release terakhir, yang kita ketahui dari tag yang dibuat ketika release.

```sh
~$ git tag #perintah untuk mengecek tag yang sudah ada
v0.1
v0.2
~$ git checkout -b hotfix0.2 v0.2# membuat branch baru dengan nama hotfix0.2 dari basis tag v0.2
```

Pada posisi ini versi source code adalah sama dengan release terakhir yang di tag di `v0.2`. Sehingga kita bisa edit versi yang sama dengan versi yang sudah di release (production).

## Lakukan edit yang diperlukan

Lakukan edit dan commit seperti di [post sebelumnya](development.md#edit-file-commit-lokal).

## Lakukan test

Test aplikasi di tier staging (sebelum production).

## Tambahkan tag hotfix

* Setelah lolos tes, maka dapat dilakukan tagging untuk versi hotfix.
* Cara melakukannya sama dengan di [release tag](#release-tag). Hanya berbeda di penomoran versi.
    * Misal pada kasus ini, kita increment di belakang versi release `.1`, sehingga dari `v0.2` menjadi `v0.2.1`.
