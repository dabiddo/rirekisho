<template>
  <div class="rirekisho-container">
    <h1 class="title">履歴書 (Rirekisho)</h1>

    <section class="personal-info">
      <h2>個人情報 (Personal Information)</h2>
      <p><strong>名前 (Name):</strong> {{ resumeData.personalInfo.kanjiName }} ({{ resumeData.personalInfo.furiganaName
        }})</p>
      <p><strong>生年月日 (Date of Birth):</strong> {{ resumeData.personalInfo.birthDate }}</p>
      <p><strong>性別 (Gender):</strong> {{ resumeData.personalInfo.gender }}</p>
      <p><strong>住所 (Address):</strong> {{ resumeData.personalInfo.address }}</p>
      <p><strong>電話番号 (Phone):</strong> {{ resumeData.personalInfo.phone }}</p>
      <p><strong>メール (Email):</strong> {{ resumeData.personalInfo.email }}</p>
      <p><strong>国籍 (Nationality):</strong> {{ resumeData.personalInfo.nationality }}</p>
      <img :src="resumeData.personalInfo.photo" alt="Profile Picture" class="profile-picture" />
    </section>

    <section class="education">
      <h2>学歴 (Education)</h2>
      <ul>
        <li v-for="(edu, index) in resumeData.education" :key="index">
          <p><strong>学校名 (Institution):</strong> {{ edu.institution }}</p>
          <p><strong>学位 (Degree):</strong> {{ edu.degree }}</p>
          <p><strong>専攻 (Major):</strong> {{ edu.major }}</p>
          <p><strong>開始日 (Start Date):</strong> {{ edu.startDate }}</p>
          <p><strong>終了日 (End Date):</strong> {{ edu.endDate || '現在' }}</p>
        </li>
      </ul>
    </section>

    <section class="work-experience">
      <h2>職歴 (Work Experience)</h2>
      <ul>
        <li v-for="(job, index) in resumeData.workExperience" :key="index">
          <p><strong>会社名 (Company):</strong> {{ job.company }}</p>
          <p><strong>役職 (Position):</strong> {{ job.position }}</p>
          <p><strong>開始日 (Start Date):</strong> {{ job.startDate }}</p>
          <p><strong>終了日 (End Date):</strong> {{ job.endDate || '現在' }}</p>
          <p><strong>概要 (Summary):</strong> {{ job.summary }}</p>
          <ul>
            <li v-for="(highlight, i) in job.highlights" :key="i">{{ highlight }}</li>
          </ul>
        </li>
      </ul>
    </section>

    <section class="skills">
      <h2>スキル (Skills)</h2>
      <ul>
        <li v-for="(skill, index) in resumeData.skills" :key="index">
          <p>{{ skill.name }} - {{ skill.level }}</p>
        </li>
      </ul>
    </section>

    <section class="languages">
      <h2>言語 (Languages)</h2>
      <ul>
        <li v-for="(lang, index) in resumeData.languages" :key="index">
          <p>{{ lang.language }} - {{ lang.fluency }}</p>
        </li>
      </ul>
    </section>

    <section class="hobbies">
      <h2>趣味 (Hobbies and Interests)</h2>
      <ul>
        <li v-for="(hobby, index) in resumeData.hobbiesAndInterests" :key="index">
          <p>{{ hobby.name }}</p>
        </li>
      </ul>
    </section>
  </div>
</template>

<script setup>
defineProps({
  resumeData: {
    type: Object,
    required: true
  }
})
</script>

<style scoped>
.rirekisho-container {
  font-family: Arial, sans-serif;
  background-color: #f9f9f9;
  padding: 20px;
  border-radius: 10px;
  max-width: 800px;
  margin: auto;
}

.title {
  text-align: center;
  color: #2c3e50;
}

.personal-info,
.education,
.work-experience,
.skills,
.languages,
.hobbies {
  margin-bottom: 20px;
}

h2 {
  color: #2980b9;
  font-size: 1.5em;
  border-bottom: 2px solid #2980b9;
  padding-bottom: 5px;
}

.profile-picture {
  max-width: 150px;
  border-radius: 50%;
  margin-top: 10px;
}

p {
  margin: 5px 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  background-color: #ecf0f1;
  padding: 10px;
  margin-bottom: 10px;
  border-radius: 5px;
}

li ul {
  margin-top: 10px;
  padding-left: 20px;
}

strong {
  color: #34495e;
}
</style>
