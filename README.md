# Instalasi

```bash
npx degit mzaini30/svelte my-project
cd my-project
npm i --prefer-offline
```

# Struktur Folder

| Keterangan | Folder |
|---|---|
| File Svelte | src/pages |
| Static files | public/dist |
| Output | public |

Hindari meletakkan file berekstensi .js, .css, dan .css.map di public. Letakkan di public/dist. Soalnya, ekstensi-ekstensi tersebut masuk di .gitignore.

# Fitur

## CSS

Menggunakan Bootstrap

## Bisa Menggunakan SASS

Contoh:

```html
<div class="container pt-3">
	<h1>Hello World</h1>
</div>

<style type="text/scss">
	$warna: red;
	$ukuran: 100px;
	h1 {
		color: $warna;
		font-size: $ukuran;
	}
</style>
```

## Bisa Juga Dibuat Global Stylenya

Contoh:

```html
<style type="text/scss" global>
	p {
		color: green;
		strong {
			text-transform: uppercase;
		}
	}
</style>
```

## Bisa Menggabungkan Global Style dan Scoped

Contoh: 

```html
<style type="text/scss">
	:global {
		p {
			color: green;
			strong {
				text-transform: uppercase;
			}
		}
		a {
			color: red;
		}
	}
	h1 {
		text-align: center;
	}
</style>
```

## Code Splitting

Cukup jalankan 

```bash
npm run build
```

## Router Berbasis File

Kita menggunakan Routify. Ini tutorialnya: https://routify.dev/guide/introduction/getting-started

## Hot Module Replacement

Dia nggak mereset state saat kita development. Cukup jalankan:

```bash
npm run dev
```

## SEO

Ini isi dari `public/index.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset='utf-8'>
	<meta name='viewport' content='width=device-width,initial-scale=1'>

	<title>Svelte Template</title>
	<meta name="description" content="Template Svelte yang diolah oleh Zen">
	<meta property="og:image" content="/dist/jean.jpg">
	<link rel='icon' type='image/png' href='/dist/ungu.png'>
	
	<meta name="twitter:card" content="summary_large_image">
	<meta name="twitter:site" content="@blogodop">
	<meta name="twitter:creator" content="@blogodop">
	<meta name="twitter:title" content="Svelte Template">
	<meta name="twitter:description" content="Template Svelte yang diolah oleh Zen">
	<meta name="twitter:image" content="https://mzaini30.js.org/dist/jean.jpg">

	<script defer src='/main.js' type="module"></script>
</head>
<body>
</body>
</html>


```

Nanti tinggal disesuaikan aja tag title, meta description, dan og image.

## Absolute Path

Contoh:

```javascript
import {nama} from '@/data/nama'
```

Tapi, bisa juga relative path seperti:

```javascript
import {nama} from '../../../nama'
```

## Tanggal

Mendapatkan tanggal terkini dengan format 2020-08-17 00:19:45

Caranya:

```html
<script>
	import {tanggal} from 'tools'
</script>
<p>{tanggal()}</p>
```

## Slug

Mendapatkan slug dari string

Caranya:

```html
<script>
	import {slug} from 'tools'
</script>
<p>{slug('hello world')}</p>
<!-- jadinya: hello-world -->
```

## Acak

Digunakan untuk mengacak array

Caranya:

```javascript
import {acak} from "tools"
let angka = [1, 2, 3, 4, 5]
angka = acak(angka)
```

## Atas

Scroll ke atas.

```javascript
import {atas} from 'tools'
atas()
```

## Clean

Membersihkan state dari kutip sehingga tidak merusak database dengan SQL Injection.

```javascript
import {clean} from 'tools'
clean('Aku mau "makan')
```

## Sleep

Memberi jeda dalam milidetik.

```javascript
import {sleep} from 'tools'
(async function(){
	console.log('Hello')
	await sleep(5000) // sleep 5 detik
	console.log('World')
})()
```

# Terjemahan?

Boleh. Misalnya aja mau nerjemahkan ke bahasa Jepang, maka buat file `README-jp.md` yang berisi terjemahan README ini dalam bahasa Jepang.
