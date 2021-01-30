<template>
  <div class="text-white bg-gradient-to-t from-black to-green-900">
    <div class="container max-w-xl">
      <div class="shadow-lg rounded-lg p-5 bg-gray-800 text-left justify-left">
        <div class="font-black text-5xl px-5 my-2">$SER</div>

        <div class="mb-3 border border-gray-700 rounded-lg py-2 px-5">
          <div class="grid grid-flow-col grid-cols-2 gap-4">
            <div>
              <label class="font-light text-sm my-2 ml-1 text-xl">From</label>
              <div>
                <input
                  class="text-3xl font-bold w-full px-3 py-2 mb-1 focus:outline-none focus:border-yellow-500 transition-colors bg-gray-800"
                  placeholder="0.0"
                  type="number"
                />
              </div>
            </div>
            <div class="text-right">
              <label class="font-light text-sm my-2 mr-5 text-xl">Balance: {{balanceFromCurrency}} </label>
              <div
                class="inline-flex  p-2 rounded-full font-bold"
              >
              <div class="text-sm font-light rounded p-1 mt-3 m-2 mr-5 bg-blue-700">
                MAX
              </div>
                <div class="text-3xl ">ETH</div>
                <div class="inline-block align-middle p-3">
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 24 24"
                    width="24"
                    height="24"
                  >
                    <path fill="none" d="M0 0h24v24H0z" />
                    <path
                      fill="#fafafa"
                      d="M12 13.172l4.95-4.95 1.414 1.414L12 16 5.636 9.636 7.05 8.222z"
                    />
                  </svg>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="m-5">
          <label class="font-light text-xl">Leverage level</label>

          <div class="grid grid-flow-col grid-cols-4 gap-4 pt-2">
            <div
              class="w-full border rounded-full text-2xl text-center "
              v-on:click="leverage=2"
              v-bind:class= "[leverage===2 ? 'bg-gradient-to-r from-yellow-600 to-green-600 font-bold' : '']"
            >
              2x
            </div>
            <div class="w-full border rounded-full text-2xl text-center"
            v-on:click="leverage=3"
              v-bind:class= "[leverage===3 ? 'bg-gradient-to-r from-yellow-600 to-green-600 font-bold' : '']"
            >
              3x
            </div>
            <div class="w-full border rounded-full text-2xl text-center"
              v-on:click="leverage=4"
              v-bind:class= "[leverage===4 ? 'bg-gradient-to-r from-yellow-600 to-green-600 font-bold' : '']"
            >
              4x
            </div>
            <div class="">
              <input
                class="w-full border outline-none rounded-full bg-gray-800 text-center text-2xl"
                v-bind:class= "[( leverage!==2 && leverage!==3 && leverage!==4) ? 'bg-gradient-to-r from-yellow-600 to-green-600 font-bold' : '']"
                placeholder="2.00"
                type="number"
                :value="(leverage!==2 && leverage!==3 && leverage!==4) ? leverage: ''"
                 @input="leverage = $event.target.value"
              />
            </div>
          </div>
        </div>

        <div class="mb-3 border border-gray-700 rounded-lg py-2 px-5">
          <div class="grid grid-flow-col grid-cols-2 gap-4">
            <div>
              <label class="font-light text-sm my-2 ml-1 text-xl">To</label>
              <div>
                <input
                  class="font-bold text-3xl w-full px-3 py-2 mb-1 focus:outline-none focus:border-yellow-500 transition-colors bg-gray-800"
                  placeholder="0.0"
                  type="number"
                />
              </div>
            </div>
            <div>
              <button
                class="w-full inline-flex justify-center mt-10 mb-2  bg-gradient-to-r from-yellow-600 to-green-600 px-5 py-2 rounded-lg font-medium"
              >
                <div class="md:text-2xl ">select token</div>
                <div class="hidden md:block inline-block align-middle p-2">
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 24 24"
                    width="24"
                    height="24"
                  >
                    <path fill="none" d="M0 0h24v24H0z" />
                    <path
                      fill="#fafafa"
                      d="M12 13.172l4.95-4.95 1.414 1.414L12 16 5.636 9.636 7.05 8.222z"
                    />
                  </svg>
                </div>
              </button>
            </div>
          </div>
        </div>
        <div>
          <button class="w-full text-4xl py-2 rounded-lg bg-gradient-to-r from-yellow-600 to-green-600 font-medium" v-on:click="executeLeverage">
            Execute
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data:() => ({
        leverage: 2,
        balanceFromCurrency: 1.213,
      }),
      methods: {
        executeLeverage: function() {
          console.log("execute");
          console.log("leverage", this.leverage)
          }
        }
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
