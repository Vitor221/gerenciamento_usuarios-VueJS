<template>
  <div class="flex flex-col h-screen">
      <div class="flex flex-1 items-center justify-around">
          <div class="">
            <form v-on:submit.prevent="addUser" class="flex justify-center items-center flex-col w-full h-full">
                <label class="text-2xl z-10 top-2 left-2 text-center">
                    Nome
                </label>

                <input type="text" v-model="newUser" class="text-center border-2 border-amber-300 outline-none rounded-2xl px-3 w-96 h-10 mt-2">

                <button class="mt-5 bg-amber-500 p-2 px-5 rounded border-2 border-amber-300 text-amber-50 font-bold text-lg hover:scale-105 transition-all ease-in-out duration-300" type="submit">
                    Cadastrar
                </button>
            </form>
          </div>

          <div class="-mt-6 border-amber-200 border-4 px-4 py-4">
              <label>Último usuário registrado: {{ users[users.length - 1].name }}</label>
              <div class="border-amber-200 border-4 px-20 py-20">
                <ul>
                    <li v-for="user in users" :key="user.id">
                        <input type="text" :value="user.name" @change="setUser($event.target.value, user.id)">
                        <button @click="removerUser(user.id)" class="py-2 px-5 bg-red-500 rounded text-amber-100 hover:bg-red-700 hover:scale-105 hover:font-bold duration-300 transition ease-in-out mt-5" >Excluir</button>
                    </li>
                </ul>
              </div>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name: 'App',
    data: () => ({
        users: [
            { id: '', name: '',}
        ],
        newUser: ''
    }),
    methods: {
        addUser() {
          this.users.push({
              id: (this.users.length + 1),
              name: this.newUser
          });

          console.log(this.users);
        },
        setUser(newName, id) {
            this.users.map(user => {
                if(user.id == id) {
                    user[name] = newName;
                }
            })
        },
        removerUser(id) {
            this.users = this.users.filter(user => {
                return(user.id != id);
            })
        }
    }
}
</script>

<style>

</style>
