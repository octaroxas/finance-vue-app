<script>
export default {
    data() {
        return {
            wallets: [
                {
                    title: 'Inter',
                    balance: 250
                },
                {
                    title: 'Inter',
                    balance: 250
                }
            ],
            transactions: [
                {
                    title: 'Gasolina',
                    value: 20,
                    category: 'Transporte'
                }
            ],
            wallet: {},
            transaction: {}
        }
    },
    methods: {
        addWallet(wallet) {
            if (wallet.title != "" && wallet.balance != "")
                this.wallets.push(wallet)
        },
        addTransaction(transaction) {
            if (transaction.title != "" && transaction.balance != "")
                this.transactions.push(transaction)
        }
    }


}
</script>

<template>
    <div class="bg-[#161B4C] pb-96">

        <header class="border-slate-700 border-b-2 shadow-lg py-5">
            <div class="p-5 lg:p-0  lg:w-2/3 lg:mx-auto">
                <h1 class="text-slate-400 text-2xl font-bold">Finance Control</h1>
            </div>
        </header>

        <main class="p-5 lg:p-0 lg:w-2/3 lg:mx-auto text-slate-400 ease-in-out duration-300">

            <div class="border-b-2 border-slate-500">
                <h1 class="font-bold my-5 text-xl">Criar Carteiras</h1>
            </div>
            <section>
                <form @submit.prevent="addWallet(transaction)" class="grid grid-cols-3 gap-2 my-5">
                    <label class="flex flex-col">
                        Titulo
                        <input required
                            class="w-56 bg-transparent rounded-lg p-2 border-[#45377D] border-2 placeholder:text-xs outline-none"
                            type="text" v-model="wallet.title" placeholder="Ex: Nubank" />
                    </label>

                    <label class="flex flex-col">
                        Saldo inicial
                        <input required
                            class="w-56 bg-transparent rounded-lg p-2 border-[#45377D] border-2 placeholder:text-xs outline-none"
                            type="number" v-model="wallet.balance" placeholder="Ex: 200" />
                    </label>

                    <div class="h-full flex items-end">
                        <button type="submit"
                            class="h-12 w-2/5 rounded-lg px-2 text-slate-50 hover:bg-indigo-700 bg-indigo-600 ease-in-out duration-300 py-2">Criar</button>
                    </div>
                </form>
            </section>

            <div id="scrollbar-wallets" class="flex overflow-x-auto py-2">
                <section>
                    <div class="bg-[#6E42EC] rounded-lg p-6 w-80 mx-1 text-white">
                        <h4>Carteira principal</h4>
                        <div class="flex flex-row-reverse mt-4">
                            <div class="flex flex-col text-right">
                                <p>Saldo</p>
                                <span>R$ 200,00</span>
                            </div>
                        </div>
                    </div>
                </section>

                <section class="flex" v-for="w in wallets" :key="index">

                    <div class="bg-[#6E42EC] rounded-lg p-6 w-80 mx-1 text-white">
                        <h4>{{ w.title }}</h4>
                        <div class="flex flex-row-reverse mt-4">
                            <div class="flex flex-col text-right">
                                <p>Saldo</p>
                                <span>R$ {{ w.balance }},00</span>
                            </div>
                        </div>
                    </div>
                </section>
            </div>

            <div class="border-b-2 border-slate-500">
                <h1 class="font-bold my-5 text-xl">Nova transação</h1>
            </div>

            <section>
                <form @submit.prevent="addTransaction(transaction)" class="grid grid-cols-3 gap-2 my-5">
                    <label class="flex flex-col">
                        Titulo
                        <input required
                            class="w-56 bg-transparent rounded-lg p-2 border-[#45377D] border-2 placeholder:text-xs outline-none"
                            type="text" v-model="transaction.title" placeholder="Ex: Nubank" />
                    </label>

                    <label class="flex flex-col">
                        Valor
                        <input required
                            class="w-56 bg-transparent rounded-lg p-2 border-[#45377D] border-2 placeholder:text-xs outline-none"
                            type="number" v-model="transaction.value" placeholder="Ex: 200" />
                    </label>

                    <label class="flex flex-col">
                        Categoria
                        <input required
                            class="w-56 bg-transparent rounded-lg p-2 border-[#45377D] border-2 placeholder:text-xs outline-none"
                            type="text" v-model="transaction.category" placeholder="Ex: 200" />
                    </label>

                    <div class="h-full flex items-end">
                        <button type="submit"
                            class="h-12 w-2/5 rounded-lg px-2 text-slate-50 hover:bg-indigo-700 bg-indigo-600 ease-in-out duration-300 py-2">Criar</button>
                    </div>
                </form>
            </section>

            <div class="border-b-2 border-slate-500">
                <h1 class="font-bold my-5 text-2xl">Movimentações</h1>
            </div>
            <section class="flex" v-for="t in transactions">

                <div class="bg-[#1C235F] flex items-center p-3 px-5 w-full">
                    <div class="flex flex-col w-11/12">
                        <pre class="text-lg font-bold">{{ t.title }}</pre>
                        <pre class="text-xs">{{ t.category }}</pre>
                    </div>

                    <div>
                        <p>R$ {{ t.value }}</p>
                    </div>
                </div>
            </section>
        </main>
    </div>
</template>