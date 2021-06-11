<template>
  <div id="app" class="w-96 my-8 mx-auto">
    <form @submit.prevent="submit" class="border border-gray-700 rounded">
      <div class="bg-indigo-800 text-white pt-6 pl-6 pb-2">
        <h1 class="text-2xl mb-6">Formulário<br>para compra de<br><span class="font-bold">Pacote de Stickers</span></h1>
      </div>
      <div class="px-4">
        <h2 class="mt-8 text-lg font-semibold">Quais stickers:</h2>
        <div class="flex flex-col space-y-2 my-2">
          <p class="mb-5">
            <input type="checkbox" id="react" value="react" v-model="check" />
            <label for="react" class="mx-2">React</label>
          </p>
          <p class="mb-5">
            <input type="checkbox" id="vue" value="vue" v-model="check" />
            <label for="vue" class="mx-2">Vue</label>
          </p>
          <p class="mb-5">
            <input type="checkbox" id="angular" value="angular" v-model="check" />
            <label for="angular" class="mx-2">Angular</label>
          </p>
        </div>
        <h2 class="mt-8 text-lg font-semibold">Quantos stickers de cada?</h2>
        <div class="my-2 flex space-x-2">
          <div class="cursor-pointer" @click.prevent="decrease">
            <svg xmlns="http://www.w3.org/2000/svg" width="42" height="42">
              <path d="M4.667 0A4.668 4.668 0 0 0 0 4.667v32.666A4.668 4.668 0 0 0 4.667 42h32.666A4.668 4.668 0 0 0 42 37.333V4.667A4.668 4.668 0 0 0 37.333 0H4.667zm28 23.333H9.333v-4.666h23.334v4.666z" />
            </svg>
          </div>
          <input type="text" name="qtd" id="qtd" :value="count" class="border border-gray-500 rounded w-32 px-2">
          <div class="cursor-pointer" @click="increase">
            <svg xmlns="http://www.w3.org/2000/svg" width="42" height="42">
              <path d="M4.667 42h32.666A4.668 4.668 0 0 0 42 37.333V4.667A4.668 4.668 0 0 0 37.333 0H4.667A4.668 4.668 0 0 0 0 4.667v32.666A4.668 4.668 0 0 0 4.667 42zm4.666-23.333h9.334V9.333h4.666v9.334h9.334v4.666h-9.334v9.334h-4.666v-9.334H9.333v-4.666z" />
            </svg>
          </div>
        </div>
        <h2 class="mt-8 text-lg font-semibold">Observações:</h2>
        <textarea name="obs" v-model="obs" id="obs" cols="45" rows="5" placeholder="Alguma dúvida? Recado?" style="resize: none;" class="rounded border border-gray-500 p-2"></textarea>
      </div>
      <div class="bg-indigo-100 mt-4 py-6 text-right pr-12">
        <button type="submit" class="border rounded bg-black text-white py-1 px-5 hover:bg-gray-700">Enviar</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data(){
    return{
      check: [],
      count: 0,
      obs: ''
    }
  },
  methods: {
    decrease(){
      this.count -= 1
    },

    increase(){
      this.count += 1
    },

    submit(){
      if(!this.check.length) alert('Selecione um sticker')
      if(this.count === 0) alert('Selecione a quantidade')
      if(this.count < 0) alert('Quantidade não pode ser negativa')
      if(!this.obs) alert('Digite a observação')

      if(this.check.length && this.count > 0 && this.obs){
        alert('Enviado com sucesso!')
        this.check.length = 0
        this.count = 0
        this.obs = ''
      }
    }
  }
}
</script>