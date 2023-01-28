<script>
	// 8桁のランダムなパスワードを10個作成する
	/**
	 * @type {string[]}
	 */
	let password = [];
	function createPassword() {
		const length = 8;
		const charset = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
		for (let create_num = 0; create_num < 10; create_num++) {
      let retVal = '';
			for (let i = 0, n = charset.length; i < length; ++i) {
				retVal += charset.charAt(Math.floor(Math.random() * n));
			}
      password[create_num] = retVal;
		}
	}
</script>

<main>
	<!-- Path: src/routes/+page.svelte -->
	<div class="detail">
		<h1>パスワードジェネレーター</h1>
		<p>自分にあったパスワードを作成出来るツールです。</p>
		<p>文字数は２~10文字の間で作成することができます。</p>
	</div>

	<div class="option-area">
		<form action="">
			<table>
				<tr>
					<th>強度</th>
					<td>
						<input type="radio" id="custom" name="strong" value="weak" checked />
						<label for="custom">カスタム</label>
						<input type="radio" id="strong" name="strong" value="weak" />
						<label for="strong">強い</label>
						<input type="radio" id="weak" name="strong" value="weak" />
						<label for="weak">弱い</label>
					</td>
				</tr>
				<tr>
					<th>文字数</th>
					<td>
						<input type="number" id="length" name="length" min="2" max="10" value="8" />
					</td>
				</tr>
			</table>
		</form>

		<div class="button-area">
			<button on:click={createPassword}>パスワードを作成する</button>
		</div>

		<div class="result-area">
			{#each password as pass}
				<p>{pass}</p>
			{/each}
		</div>
	</div>
</main>
