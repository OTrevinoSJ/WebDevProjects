<script lang="ts">
	import { onMount } from 'svelte';

	interface fontObj {
		text: string;
		color: string;
	}

	const logoTexts: Array<fontObj> = [
		{ text: 'Retro™', color: '264653' },
		{ text: 'レトロ™', color: '2A9D8F' },
		{ text: 'Rétro™', color: 'E9C46A' },
		{ text: 'ย้อนยุค™', color: 'F4A261' },
		{ text: '复古™', color: 'E76F51' }
	];
	const homeTexts: Array<fontObj> = [
		{ text: 'Home', color: '264653' },
		{ text: 'ホーム', color: '2A9D8F' },
		{ text: 'Accueil', color: 'E9C46A' },
		{ text: '主頁', color: 'F4A261' },
		{ text: 'Ev', color: 'E76F51' }
	];
	const infoTexts: Array<fontObj> = [
		{ text: 'Info', color: '264653' },
		{ text: '情報', color: '2A9D8F' },
		{ text: 'Info', color: 'E9C46A' },
		{ text: '信息', color: 'F4A261' },
		{ text: 'Bilgi', color: 'E76F51' }
	];
	const jobsTexts: Array<fontObj> = [
		{ text: 'Jobs', color: '264653' },
		{ text: '仕事', color: '2A9D8F' },
		{ text: 'Emplois', color: 'E9C46A' },
		{ text: 'Töökohad', color: 'F4A261' },
		{ text: '喬布斯', color: 'E76F51' }
	];
	const contactTexts: Array<fontObj> = [
		{ text: 'Contact', color: '264653' },
		{ text: '連絡先', color: '2A9D8F' },
		{ text: 'Kontakt', color: 'E9C46A' },
		{ text: '聯繫', color: 'F4A261' },
		{ text: 'İletişim', color: 'E76F51' }
	];
	let spanText: HTMLSpanElement;
	let intervalId: number;
	let intervalIdClass: number;

	let homeElement: HTMLParagraphElement;
	let infoElement: HTMLParagraphElement;
	let jobsElement: HTMLParagraphElement;
	let contactElement: HTMLParagraphElement;

	function switchLangs(spanText: HTMLElement, langTexts: Array<fontObj>) {
		spanText.classList.add('active-hover');

		intervalIdClass = setInterval(() => {
			if (spanText.classList.contains('active-hover')) {
				spanText.classList.toggle('active-hover');
			} else {
				spanText.classList.add('active-hover');
			}
		}, 3000);

		let i = 0;
		if (i < langTexts.length) {
			intervalId = setInterval(() => {
				if (i < langTexts.length) {
					spanText.textContent = langTexts[i].text;
					spanText.style.color = '#' + langTexts[i].color;
					i += 1;
				} else {
					i = 0;
				}
			}, 500);
		}
	}

	function resetLang(spanText: HTMLElement, langTexts: Array<fontObj>) {
		clearInterval(intervalIdClass);
		clearInterval(intervalId);

		if (spanText.classList.contains('active-hover')) spanText.classList.toggle('active-hover');

		spanText.textContent = langTexts[0].text;
		spanText.style.color = 'black';
	}
</script>

<header>
	<div>
		<a href="https://www.merriam-webster.com/dictionary/retro">
			<span
				role="figure"
				bind:this={spanText}
				onmouseenter={() => switchLangs(spanText, logoTexts)}
				onmouseleave={() => resetLang(spanText, logoTexts)}
				class="active-hover">Retro&#8482;</span
			>
		</a>
	</div>

	<ul>
		<li>
			<a href="https://www.merriam-webster.com/dictionary/home"
				><p
					bind:this={homeElement}
					onmouseenter={() => switchLangs(homeElement, homeTexts)}
					onmouseleave={() => resetLang(homeElement, homeTexts)}
				>
					Home
				</p></a
			>
		</li>
		<li>
			<a href="https://www.merriam-webster.com/dictionary/info"
				><p
					bind:this={infoElement}
					onmouseenter={() => switchLangs(infoElement, infoTexts)}
					onmouseleave={() => resetLang(infoElement, infoTexts)}
				>
					Info
				</p></a
			>
		</li>
		<li>
			<a href="https://www.merriam-webster.com/dictionary/Jobs"
				><p
					bind:this={jobsElement}
					onmouseenter={() => switchLangs(jobsElement, jobsTexts)}
					onmouseleave={() => resetLang(jobsElement, jobsTexts)}
				>
					Jobs
				</p></a
			>
		</li>
		<li>
			<a href="https://www.merriam-webster.com/dictionary/contact"
				><p
					bind:this={contactElement}
					onmouseenter={() => switchLangs(contactElement, contactTexts)}
					onmouseleave={() => resetLang(contactElement, contactTexts)}
				>
					Contact
				</p></a
			>
		</li>
	</ul>
</header>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@100..900&display=swap');

	header {
		display: flex;
		justify-content: space-between;

		padding: 4rem;
	}

	header span {
		display: block;
		cursor: pointer;
		font-size: x-large;
		transition: all 1s ease-in-out;
	}

	span.active-hover:hover {
		font-weight: bolder;
		opacity: 0.5;
		transform: scale(1.5);
		color: red;
	}

	header div {
		padding: 1rem;
	}

	header ul li {
		transition: all 250ms ease-in;
		padding-bottom: 0.5rem;
		border-radius: 0.5rem;
	}

	ul li:hover {
		border-bottom: 1rem solid;
	}

	ul li:first-child:hover {
		border-color: #264653;
	}

	ul li:nth-child(2):hover {
		border-color: #2a9d8f;
	}

	ul li:nth-child(3):hover {
		border-color: #e9c46a;
	}

	ul li:last-child:hover {
		border-color: #e76f51;
	}

	ul {
		display: flex;
		gap: 4rem;

		padding: 1rem;
		list-style: none;
	}
</style>
