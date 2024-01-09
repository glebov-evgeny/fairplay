<template>
  <section class="s-reg">
    <div class="s-reg__container">
      <h1 class="s-reg__title">Регистрация</h1>
      <span>{{ currentUser }}</span>
      <div class="s-reg__formbox">
        <form class="s-reg__form" :submit-disabled="!validFlag" @submit.prevent="sendForm">
          <label class="s-reg__form-label">
            <input v-model="fieldsData.name" class="s-reg__form-input" type="text" placeholder="Имя" />
          </label>
          <label class="s-reg__form-label">
            <input v-model="fieldsData.password" class="s-reg__form-input" type="password" placeholder="Пароль" />
          </label>
          <button type="submit" class="s-reg__form-button">Регистрация</button>
        </form>
      </div>
    </div>
  </section>
</template>

<script setup>
import { useUserStore } from '~/store/user';
const currentUser = useUserStore();
// const router = useRouter();
// const userInformation = useCookie('userInformation', {
//   default: () => null,
//   watch: 'shallow',
// });

let fieldsData = reactive({
  name: '',
  password: '',
});

let validFlag = ref(false);

// const checkedValidateError = () => {
//   return console.log('send???');
//   // return fieldsData.name === '12345' && fieldsData.password === '12345' ? true : false;
// };

// watch(
//   fieldsData,
//   () => {
//     validFlag.value = checkedValidateError();
//   },
//   { immediate: true },
// );

// async function sendForm() {
//   if (validFlag.value === true) {
//     currentUser.setUser(fieldsData.name, fieldsData.password);
//     /* устанавливаю куки с почтой и id пользователя на 7 дней */
//     const cookieDataUser = {
//       email: fieldsData.name,
//       id: fieldsData.password,
//       maxAge: 60 * 60 * 24 * 7,
//     };
//     userInformation.value = cookieDataUser;
//     router.push({ path: '/admin' });
//   } else {
//     console.log('что-то пошло не так');
//   }
// }
import { getAuth, createUserWithEmailAndPassword } from '@firebase/auth';
// import { initializeApp } from 'firebase/app';
// import { firebaseConfig } from './firebase/firebaseConfig';

async function sendForm() {
  // console.log(getAuth);
  const auth = getAuth();
  try {
    const user = await createUserWithEmailAndPassword(auth, 'ccsdcsdsdcs@mail.ru', 'csdcsdcsdcACssa23');
    console.log(user);
  } catch (error) {
    if (error.message === 'Firebase: Error (auth/wrong-password).') {
      console.log('Неправильный логин/пароль.');
    } else {
      console.error(`Ошибка: ${error.message}`);
    }
  }
}
async function sendForm2() {
  console.log('жамк');
  currentUser.setUser(fieldsData.name, fieldsData.password, fieldsData.password);
}
</script>

<style lang="scss">
@import './s-reg.scss';
</style>
