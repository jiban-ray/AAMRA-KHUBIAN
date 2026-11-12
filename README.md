# আমরা খুবি’য়ান — ওয়েবসাইট সম্পাদনার নির্দেশনা

এটি একটি static website। GitHub-এর ওয়েব ইন্টারফেস দিয়েই লেখা ও ছবি পরিবর্তন করা যায়। প্রতিটি পরিবর্তনের পরে **Commit changes** করতে হবে। GitHub Pages বা সংযুক্ত Netlify নতুন সংস্করণ প্রকাশ করবে।

## ১. ইশতেহারের PDF পরিবর্তন

বর্তমান PDF: `documents/KUAA_Election_2026_Manifesto.pdf`। GitHub-এ `documents` ফোল্ডার খুলে পুরোনো PDF মুছে একই **নাম ও extension** দিয়ে নতুন PDF Upload করুন। তারপর Commit করুন। `manifesto.json`-এর `pdf` ফিল্ডে এই পথ দেওয়া আছে; একই নাম রাখলে ওয়েবসাইটে অন্য কিছু পরিবর্তন করতে হবে না। ভিন্ন নামে PDF দিলে `manifesto.json`-এর `pdf` ফিল্ডেও নতুন পথ লিখতে হবে।

**মনে রাখবেন:** ওয়েবসাইটে দৃশ্যমান ৮টি অঙ্গীকার ও সময়সূচির লেখা আলাদাভাবে `manifesto.json`-এ আছে। PDF বদলালে সেই লেখা স্বয়ংক্রিয়ভাবে বদলাবে না। লেখাও পরিবর্তন করতে হলে `manifesto.json` সম্পাদনা করুন।

## ২. প্রার্থীর ছবি পরিবর্তন

`images/candidates/`-এ ছবিগুলো আছে। যেমন `970526.jpg` হলো Liton-এর ছবি। একই নামে নতুন JPG আপলোড করে পুরোনোটি Replace করলে কার্ড ও বিস্তারিত পরিচিতিতে নতুন ছবি দেখাবে। ছবির নাম বা extension পরিবর্তন করলে `index.html`-এ `const candidates=` অংশে সংশ্লিষ্ট প্রার্থীর `photo` পথও বদলাতে হবে। ছবির জন্য portrait 3:4 ratio সুবিধাজনক।

## ৩. বিস্তারিত পরিচিতি ও কার্যক্রমের ছবি যোগ

`profiles.json` ফাইল সম্পাদনা করুন। `profiles_TEMPLATE.json`-এ **খালি নমুনা** রয়েছে; এটি ওয়েবসাইটে স্বয়ংক্রিয়ভাবে প্রকাশ হয় না। Student ID (roll) key দিয়ে প্রার্থীর তথ্য যুক্ত করুন। উদাহরণ:

```json
{
  "970526": {
    "profession": "পেশাগত পরিচিতি লিখুন",
    "organization": "সাংগঠনিক অভিজ্ঞতা লিখুন",
    "socialWelfare": "সামাজিক ও কল্যাণমূলক কাজ লিখুন",
    "kuaaInvolvement": "কবে থেকে KUAA-র সঙ্গে যুক্ত ও কী কাজ করেছেন",
    "membershipStatus": "সদস্যপদের যাচাইকৃত তথ্য লিখুন",
    "other": "অন্যান্য তথ্য",
    "activityPhotos": ["images/activity/970526-event1.jpg"]
  }
}
```

এটি **শুধু উদাহরণ**—প্রকাশের আগে প্রকৃত যাচাইকৃত তথ্য লিখুন। `images/activity/`-তে `970526-event1.jpg` নামের ছবি আপলোড করুন। আরও ছবি চাইলে `activityPhotos` array-তে আরও path যোগ করুন। `profiles.json`-এ একাধিক প্রার্থীর তথ্য যোগ করলে প্রতিটি entry-র মাঝে comma রাখুন। JSON-এ শেষ entry-র পরে comma দেবেন না। `বিস্তারিত পরিচিতি` বাটনে এই তথ্য ও ছবিগুলো দেখা যাবে।

## ৪. প্রার্থীর নাম, রোল, পদ পরিবর্তন

`index.html`-এ `const candidates=` খুঁজুন। সংশ্লিষ্ট candidate object-এর `name`, `roll`, `role`, `discipline`, `nick`, `photo` পরিবর্তন করুন। **গুরুত্বপূর্ণ:** `data.json` ফাইলটি তথ্যের আলাদা কপি; ওয়েবসাইট বর্তমানে `index.html`-এর embedded `candidates` ব্যবহার করে। তথ্য সামঞ্জস্য রাখতে `data.json`-এও একই সংশোধন করুন।

## ৫. GitHub-এ আপডেট প্রকাশ

1. Repository `Amra_Khubian_KUAA_2026` খুলুন।
2. টেক্সট ফাইল পরিবর্তন: ফাইল খুলে পেন্সিল **Edit this file** → পরিবর্তন → **Commit changes**।
3. ছবি/PDF বদলানো: একই path ও filename-এ নতুন ফাইল upload করুন, GitHub যদি replacement না নেয় তবে পুরোনোটি Delete করে নতুনটি Upload করুন; Commit করুন।
4. **Actions** ট্যাবে deployment status দেখুন। **Settings → Pages**-এ প্রকাশিত URL পাওয়া যাবে।
5. যদি Netlify GitHub-এর সঙ্গে connected থাকে, Commit-এর পরে স্বয়ংক্রিয়ভাবে নতুন deployment হবে।

GitHub Pages ও Netlify-তে folder structure অপরিবর্তিত রাখুন। ZIP-এর ভেতরের ফাইলগুলো repository root-এ রাখুন, nested folder-এর মধ্যে নয়।
