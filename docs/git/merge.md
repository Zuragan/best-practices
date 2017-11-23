# Merge ke Master

Merge ke master branch dilakukan oleh maintainer, untuk memastikan minimal konflik di repository, terutama jika developer lebih dari 1 orang.

## Local Merge (disarankan)

Local merge disarankan karena kita dapat melakukan merge `fast forward`, sehingga tidak perlu membuat `merge commit` kosong yang dapat mengakibatkan merge bubble, yang membuat kompleks ketika kita akan melakukan tracing bug di history commit (`bisect`).

### Fetch

Fetch, kemudian checkout feature branch di lokal

```sh
~$ git fetch
~$ git checkout -b nama-fitur origin/nama-fitur
```

### Checkout dan Merge

Pastikan master sudah terupdate dengan remote master seperti disebutkan di [sini](development.md#fetch-rebase-master). Kemudian lakukan merge branch feature.

```sh
~$ git checkout master
~$ git merge nama-fitur
```

### Push ke remote master

```sh
~$ git push origin master
```

## Remote Merge (apabila terpaksa)

Remote merge kurang disarankan karena di Codebase tidak ada opsi merge dengan `fast forward`, sehingga mau tidak mau akan terbentuk merge bubble.


### Step by step

* Buka merge request yang akan di merge
* Klik tombol *Perform Merge*


