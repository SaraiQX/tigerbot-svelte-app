<script>
	let inputValue = '';
	let response = '';
  
	async function submitInput() {
	  console.log('Submitted input:', inputValue);
  
	  try {
		const url = 'https://api.tigerbot.com/bot-service/ai_service/gpt';
		const options = {
		  method: 'POST',
		  headers: {
			'Authorization': 'Bearer ' + 'API_KEY',
			'Content-Type': 'application/json'
		  },
		  body: JSON.stringify({
			text: inputValue,
			modelVersion: 'tigerbot-7b-sft'
		  })
		};
		const result = await fetch(url, options);
		const data = await result.json();
		response = data.data.result[0];
	  } catch (error) {
		console.error(error);
		response = 'Error: Unable to connect to the server.';
	  }
	}
  </script>
  
  <section>
	<main>
	  <h1>🤖Chatbot powered by TigerBot🐯</h1>
	  <div class="input-container">
		<input type="text" class="input" bind:value={inputValue} placeholder="输入你的问题">
		<button class="button" on:click={submitInput}>提交问题</button>
	  </div>
			
	  <div class="output-container">
	  <textarea class="output" bind:value={response} placeholder="等待回答"/>
	  </div>

	</main>
  </section>


 
  <style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		width: 100%;
	}

	.input-container {
	  display: flex;
	  align-items: center;
	  width: 100%;
	  max-width: 600px;
	  margin: 10px;
	}

	.output-container {
	  display: flex;
	  align-items: center;
	  width: 100%;
	  margin: 10px;
	}
  
	.input {
	  flex-grow: 1;
	  padding: 12px;
	  font-size: 16px;
	  border: 1px solid #ccc;
	  border-radius: 4px;
	  outline: none;
	}
	.output {
	  flex-grow: 1;
	  padding: 12px;
	  font-size: 16px;
	  border: 1px solid #ccc;
	  border-radius: 4px;
	  outline: none;
	}
	.button {
	  margin-left: 12px;
	  padding: 12px;
	  font-size: 16px;
	  color: #fff;
	  background-color: #007bff;
	  border: none;
	  border-radius: 4px;
	  cursor: pointer;
	  outline: none;
	  transition: background-color 0.3s ease;
	}
  
	.button:hover {
	  background-color: #006fe6;
	}


  
  </style>