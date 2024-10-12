<template>
  <div class="max-w-4xl mx-auto my-10 p-8 bg-white rounded-lg shadow-md print-page">
    <header class="mb-8 text-center">
      <h1 class="text-3xl font-bold">履歴書</h1>
    </header>

    <!-- Personal Information -->
    <section class="mb-6">
      <h2 class="text-xl font-semibold mb-4">個人情報</h2>
      <div class="flex mb-6">
        <div class="w-1/3">
          <img v-if="basics.image" :src="basics.image" alt="写真" class="w-32 h-40 object-cover border border-gray-300">
        </div>
        <div class="w-2/3">
          <table class="w-full table-auto border-collapse border border-gray-300">
            <tbody>
              <tr>
                <td class="border border-gray-300 p-2">名前</td>
                <td class="border border-gray-300 p-2">{{ basics.name }}</td>
                <td class="border border-gray-300 p-2">ふりがな</td>
                <td class="border border-gray-300 p-2">{{ furigana }}</td>
              </tr>
              <tr>
                <td class="border border-gray-300 p-2">生年月日</td>
                <td class="border border-gray-300 p-2">{{ dob }}</td>
                <td class="border border-gray-300 p-2">性別</td>
                <td class="border border-gray-300 p-2">{{ gender }}</td>
              </tr>
              <tr>
                <td class="border border-gray-300 p-2">住所</td>
                <td colspan="3" class="border border-gray-300 p-2">{{ address }}</td>
              </tr>
              <tr>
                <td class="border border-gray-300 p-2">電話番号</td>
                <td class="border border-gray-300 p-2">{{ phone }}</td>
                <td class="border border-gray-300 p-2">メールアドレス</td>
                <td class="border border-gray-300 p-2">{{ basics.email }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </section>

    <!-- Education -->
    <section class="mb-6">
      <h2 class="text-xl font-semibold mb-4">学歴</h2>
      <table class="w-full table-auto border-collapse border border-gray-300">
        <tbody>
          <tr v-for="education in education" :key="education.institution">
            <td class="border border-gray-300 p-2">開始日</td>
            <td class="border border-gray-300 p-2">{{ education.start.year }}-{{ education.start.month }}</td>
            <td class="border border-gray-300 p-2">終了日</td>
            <td class="border border-gray-300 p-2">{{ education.end.year }}-{{ education.end.month }}</td>
          </tr>
          <tr v-for="education in education" :key="education.institution">
            <td class="border border-gray-300 p-2">学校名・学部・学科</td>
            <td colspan="3" class="border border-gray-300 p-2">{{ education.institution }} {{ education.area }}</td>
          </tr>
        </tbody>
      </table>
    </section>

    <!-- Work Experience -->
    <section class="mb-6">
      <h2 class="text-xl font-semibold mb-4">職歴</h2>

      <!-- Loop through work experiences -->
      <div v-for="workEntry in work" :key="workEntry.company" class="mb-6">
        <table class="w-full table-auto border-collapse border border-gray-300 mb-4">
          <tbody>
            <!-- Job period row -->
            <tr>
              <td class="border border-gray-300 p-2">開始日</td>
              <td class="border border-gray-300 p-2">{{ workEntry.start.year }}-{{ workEntry.start.month }}</td>
              <td class="border border-gray-300 p-2">終了日</td>
              <td class="border border-gray-300 p-2">{{ workEntry.isCurrentRole ? '現在' : workEntry.end.year + '-' +
                workEntry.end.month }}</td>
              <td class="border border-gray-300 p-2">{{ workEntry.start.year }}-{{ workEntry.start.month }}
                ({{ calculateDuration(workEntry.start, workEntry.end) }})
              </td>

            </tr>

            <!-- Company and Position row -->
            <tr>
              <td class="border border-gray-300 p-2">会社名・部署・役職</td>
              <td colspan="3" class="border border-gray-300 p-2">{{ workEntry.company }} {{ workEntry.position }}</td>
            </tr>

            <!-- Job Summary row -->
            <tr>
              <td class="border border-gray-300 p-2">仕事内容</td>
              <td colspan="3" class="border border-gray-300 p-2">{{ workEntry.summary }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </section>


    <!-- Skills -->
    <section v-if="skills && skills.length" class="mb-6">
      <h2 class="text-xl font-semibold mb-4">スキル</h2>
      <table class="w-full table-auto border-collapse border border-gray-300">
        <tbody>
          <tr v-for="skill in skills" :key="skill.name">
            <td class="border border-gray-300 p-2">{{ skill.name }}</td>
            <td class="border border-gray-300 p-2">{{ skill.level }}</td>
          </tr>
        </tbody>
      </table>
    </section>

    <!-- Additional Information -->
    <section>
      <h2 class="text-xl font-semibold mb-4">その他</h2>
      <table class="w-full table-auto border-collapse border border-gray-300">
        <tbody>
          <tr>
            <td class="border border-gray-300 p-2">自己PR・志望動機</td>
            <td class="border border-gray-300 p-2">{{ basics.summary }}</td>
          </tr>
        </tbody>
      </table>
    </section>
  </div>
</template>

<script>
export default {
  props: {
    resumeData: Object
  },
  computed: {
    basics() {
      return this.resumeData.basics;
    },
    education() {
      return this.resumeData.education;
    },
    work() {
      return this.resumeData.work;
    },
    skills() {
      return this.resumeData.skills;
    },
    furigana() {
      return ''; // Add furigana if available in the data
    },
    dob() {
      if (this.resumeData.basics.dob) {
        const [year, month, day] = this.resumeData.basics.dob.split('-');
        return `${year}年${month}月${day}日`;
      }
      return '';
    },
    gender() {
      return ''; // Add gender if available in the data
    },
    address() {
      const location = this.resumeData.basics.location || {};
      return `${location.city || ''}, ${location.state || ''}, ${location.country || ''}`;
    },
    phone() {
      return this.basics.phone || '';
    }
  },
  methods: {
    calculateDuration(start, end) {
      if (!end || start.isCurrentRole) return '現在まで';
      const startDate = new Date(start.year, start.month - 1);
      const endDate = new Date(end.year, end.month - 1);
      const durationInMonths = (endDate.getFullYear() - startDate.getFullYear()) * 12 + (endDate.getMonth() - startDate.getMonth());
      return `${Math.floor(durationInMonths / 12)}年 ${durationInMonths % 12}ヶ月`;
    }
  }

}


</script>

<style scoped>
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

  table {
    border-color: #000;
  }

  .text-center {
    text-align: center;
  }

  .no-print {
    display: none !important;
  }

}
</style>
