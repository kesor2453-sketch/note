# Rx Clinic · វេជ្ជបញ្ជា

កម្មវិធីវេបសម្រាប់គ្លីនិក៖ គំរូវេជ្ជបញ្ជាតាមក្រុមជំងឺ រោគវិនិច្ឆ័យ ICD-10 (ខ្មែរ · English · Français) និងស្តុកថ្នាំ។
A web app for clinics: prescription templates by disease group, ICD-10 diagnoses in Khmer, English and French, and drug stock.

## មុខងារ · Features

- **វេជ្ជបញ្ជា** — Consultation note (C/O, H/O, Vital signs, Dx, Ix) និងតារាងថ្នាំ ព្រឹក · ថ្ងៃ · ល្ងាច · យប់ គណនាសរុបស្វ័យប្រវត្តិ (គ្រាប់, ml → ដប, លាប → ទីប, អំពូល/ដប)
- **គំរូ ៩៣** ក្នុងក្រុមជំងឺ ១៩ ជាមួយការណែនាំជាភាសាខ្មែរ និង English
- **ស្វែងរក** តាមរោគសញ្ញា រោគវិនិច្ឆ័យ ឬកូដ ICD-10 ជា ៣ ភាសា។ នាំចូលបញ្ជី ICD-10 ពេញលេញពី Excel/CSV (ជួរឈរ ICD 10 · EN · KH · FR)
- **ស្តុកថ្នាំ** — បញ្ជីថ្នាំចាំបាច់ ១០៧ មុខ ចែកតាមប្រភេទ, ពិនិត្យ Brand/Generic ពេលសរសេរវេជ្ជបញ្ជា, ណែនាំថ្នាំជំនួស, បញ្ជីត្រូវទិញ
- **⚙ កំណត់** — ឈ្មោះគ្លីនិក អាសយដ្ឋាន ទូរស័ព្ទ វេជ្ជបណ្ឌិត ក្រដាស A5/A4, Backup/Restore
- ដំឡើងលើទូរស័ព្ទបានដូចកម្មវិធី ហើយប្រើបានពេលគ្មានអ៊ីនធឺណិត

## ទិន្នន័យ · Your data

- **គ្មាន Firebase:** ទិន្នន័យ (គំរូ, ស្តុក, ការកំណត់) រក្សាទុកក្នុង browser របស់អ្នកប្រើម្នាក់ៗ។ ប្រើ ⚙ កំណត់ → នាំចេញ / នាំចូល ដើម្បីផ្ទេរ។
- **មាន Firebase:** គំរូ ស្តុក និងការកំណត់ ធ្វើសមកាលកម្មរវាងបុគ្គលិកទាំងអស់ក្នុងគ្លីនិក ហើយនៅតែប្រើបានពេលគ្មានអ៊ីនធឺណិត។
- ព័ត៌មានអ្នកជំងឺ (ឈ្មោះ អាយុ Vital signs …) **មិនត្រូវបានរក្សាទុក ឬផ្ញើទៅណាទេ**។ បញ្ជី ICD-10 ដែលនាំចូល នៅតែក្នុងឧបករណ៍នីមួយៗ។

## ភ្ជាប់ Firebase · Connect Firebase (ឥតគិតថ្លៃ Spark plan)

1. ចូល <https://console.firebase.google.com> → **Add project** (បិទ Google Analytics ក៏បាន)
2. **Build → Firestore Database → Create database** → ជ្រើសទីតាំងជិត (ឧ. `asia-southeast1` Singapore) → Production mode
3. ផ្ទាំង **Rules** → លុបអក្សរចាស់ → បិទភ្ជាប់ខ្លឹមសារឯកសារ `firestore.rules` → **Publish**
4. **Build → Authentication → Get started → Sign-in method** → បើក **Google** និង/ឬ **Email/Password**
5. **Authentication → Settings → Authorized domains → Add domain** → `ឈ្មោះរបស់អ្នក.github.io`
6. **Project settings (⚙) → Your apps → Web (</>)** → ចុះឈ្មោះ app → ចម្លង `firebaseConfig`
7. បើកវេប → **⚙ កំណត់ → ☁ ទិន្នន័យរួម** → បិទភ្ជាប់ config → ដាក់ Clinic ID (ឧ. `clinic-phnompenh`) → **ចូលដោយ Google** → **បង្កើតគ្លីនិកថ្មី** (អ្នកក្លាយជាម្ចាស់ ហើយគំរូ និងស្តុកក្នុងឧបករណ៍របស់អ្នកត្រូវបាន upload)
8. បន្ថែម email បុគ្គលិកក្នុង **សមាជិក**។ បុគ្គលិកបិទភ្ជាប់ config ដូចគ្នា ដាក់ Clinic ID ដូចគ្នា ចូលគណនី ហើយចុច **ភ្ជាប់គ្លីនិក**

**ជម្រើស:** ដើម្បីកុំឱ្យបុគ្គលិកត្រូវបិទភ្ជាប់ config កែក្នុង `index.html` បន្ទាត់ `var FIREBASE_CONFIG=null, FIREBASE_CLINIC="";` ជា
`var FIREBASE_CONFIG={apiKey:"…",authDomain:"…",projectId:"…",appId:"…"}, FIREBASE_CLINIC="clinic-phnompenh";`
(Firebase web config មិនមែនជាលេខសម្ងាត់ទេ។ សុវត្ថិភាពពឹងលើ Rules និងការចូលគណនី។)

## ដាក់លើ GitHub Pages · Publish on GitHub Pages

1. បង្កើត repository ថ្មីលើ GitHub (Public)
2. Upload ឯកសារទាំងអស់ក្នុង folder នេះ (`index.html`, `manifest.webmanifest`, `sw.js`, `icon-*.png`, `apple-touch-icon.png`, `.nojekyll`; `firestore.rules` សម្រាប់ចម្លងទៅ Firebase)
3. **Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch: `main` / `(root)` → Save**
4. ក្រោយ ១–២ នាទី វេបនឹងនៅ `https://<username>.github.io/<repository>/`

## ដំឡើងលើទូរស័ព្ទ · Install on a phone

- **Android (Chrome):** បើកតំណ → ⋮ → *Add to Home screen / Install app*
- **iPhone (Safari):** បើកតំណ → Share → *Add to Home Screen*

## ចំណាំ · Note

ដូសថ្នាំ ការបកប្រែ និងបញ្ជីថ្នាំចាំបាច់ ជាគំរូចាប់ផ្តើមប៉ុណ្ណោះ។ វេជ្ជបណ្ឌិតត្រូវពិនិត្យ និងកែតាមគោលការណ៍ណែនាំរបស់ក្រសួងសុខាភិបាល មុនប្រើជាមួយអ្នកជំងឺ។
Doses, translations and the starter drug list are a starting point; a doctor must review them against national guidelines before clinical use.
