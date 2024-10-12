<template>
  <!DOCTYPE html>
  <html lang="ja">

  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>履歴書</title>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">

  </head>

  <body class="bg-gray-100 text-gray-900">
    <div class="max-w-4xl mx-auto my-10 p-8 bg-white rounded-lg shadow-md print-page">
      <header class="mb-8 text-center">
        <h1 class="text-3xl font-bold">履歴書</h1>
      </header>

      <!-- Personal Information -->
      <section class="mb-6">
        <h2 class="text-xl font-semibold mb-4">個人情報</h2>
        <div class="grid grid-cols-2 gap-4">
          <div>
            <label class="block text-sm font-medium text-gray-700">名前</label>
            <input type="text" class="mt-1 p-2 w-full border rounded-md" placeholder="山田 太郎">
          </div>
          <div>
            <label class="block text-sm font-medium text-gray-700">ふりがな</label>
            <input type="text" class="mt-1 p-2 w-full border rounded-md" placeholder="やまだ たろう">
          </div>
          <div>
            <label class="block text-sm font-medium text-gray-700">生年月日</label>
            <input type="date" class="mt-1 p-2 w-full border rounded-md">
          </div>
          <div>
            <label class="block text-sm font-medium text-gray-700">性別</label>
            <select class="mt-1 p-2 w-full border rounded-md">
              <option>男性</option>
              <option>女性</option>
              <option>その他</option>
            </select>
          </div>
          <div class="col-span-2">
            <label class="block text-sm font-medium text-gray-700">住所</label>
            <input type="text" class="mt-1 p-2 w-full border rounded-md" placeholder="東京都千代田区1-1-1">
          </div>
          <div>
            <label class="block text-sm font-medium text-gray-700">電話番号</label>
            <input type="tel" class="mt-1 p-2 w-full border rounded-md" placeholder="090-1234-5678">
          </div>
          <div>
            <label class="block text-sm font-medium text-gray-700">メールアドレス</label>
            <input type="email" class="mt-1 p-2 w-full border rounded-md" placeholder="example@example.com">
          </div>
        </div>
      </section>

      <!-- Education -->
      <section class="mb-6">
        <h2 class="text-xl font-semibold mb-4">学歴</h2>
        <div class="grid grid-cols-2 gap-4">
          <div>
            <label class="block text-sm font-medium text-gray-700">開始日</label>
            <input type="month" class="mt-1 p-2 w-full border rounded-md">
          </div>
          <div>
            <label class="block text-sm font-medium text-gray-700">終了日</label>
            <input type="month" class="mt-1 p-2 w-full border rounded-md">
          </div>
          <div class="col-span-2">
            <label class="block text-sm font-medium text-gray-700">学校名・学部・学科</label>
            <input type="text" class="mt-1 p-2 w-full border rounded-md" placeholder="東京大学 法学部">
          </div>
        </div>
      </section>

      <!-- Work Experience -->
      <section class="mb-6">
        <h2 class="text-xl font-semibold mb-4">職歴</h2>
        <div class="grid grid-cols-2 gap-4">
          <div>
            <label class="block text-sm font-medium text-gray-700">開始日</label>
            <input type="month" class="mt-1 p-2 w-full border rounded-md">
          </div>
          <div>
            <label class="block text-sm font-medium text-gray-700">終了日</label>
            <input type="month" class="mt-1 p-2 w-full border rounded-md">
          </div>
          <div class="col-span-2">
            <label class="block text-sm font-medium text-gray-700">会社名・部署・役職</label>
            <input type="text" class="mt-1 p-2 w-full border rounded-md" placeholder="株式会社ABC 営業部 部長">
          </div>
          <div class="col-span-2">
            <label class="block text-sm font-medium text-gray-700">仕事内容</label>
            <textarea class="mt-1 p-2 w-full border rounded-md" rows="3" placeholder="仕事内容を簡潔に記載してください"></textarea>
          </div>
        </div>
      </section>

      <!-- Skills -->
      <section class="mb-6">
        <h2 class="text-xl font-semibold mb-4">スキル</h2>
        <div class="grid grid-cols-1 gap-4">
          <div>
            <label class="block text-sm font-medium text-gray-700">スキル・資格</label>
            <input type="text" class="mt-1 p-2 w-full border rounded-md" placeholder="例: プログラミング, 英語">
          </div>
        </div>
      </section>

      <!-- Additional Information -->
      <section>
        <h2 class="text-xl font-semibold mb-4">その他</h2>
        <div>
          <label class="block text-sm font-medium text-gray-700">自己PR・志望動機</label>
          <textarea class="mt-1 p-2 w-full border rounded-md" rows="5" placeholder="自己PRや志望動機を記載してください"></textarea>
        </div>
      </section>
    </div>
  </body>

  </html>


</template>
<style>
@media print {
  body {
    background-color: white;
    color: black;
  }

  .print-page {
    margin: 0;
    box-shadow: none;
  }

  header,
  footer {
    display: none;
  }
}
</style>