<script lang="ts">
	import { fade } from 'svelte/transition';
	import ButtonLink from '../Common/ButtonLink.svelte';
	import Navigation from '../Common/Navigation.svelte';
	import { onMount } from 'svelte';

	let ready = false;
	let animationIndex = 1;
	onMount(() => (ready = true));
	setInterval(() => {
		if (ready && animationIndex < 10) {
			animationIndex++;
		}
	}, 500);
	$: animateIn = (targetIndex: number, animation: string) => {
		return targetIndex >= animationIndex ? 'hidden' : animation;
	};
</script>

<div class="section-container">
	<div class="section">
		<p class={'greeting ' + animateIn(1, 'fade')} transition:fade>
			Hi, I'm <span class="greeting-name">Job Lipat</span>.
		</p>
		<p class={'info ' + animateIn(2, 'fade')}>
			I'm a B.S. Computer Science graduate from Mapua Malayan Colleges Laguna.
		</p>
		<p class={'subinfo ' + animateIn(3, 'fade')}>
			Problem Solver at heart, Software Engineer by profession.
		</p>
		<div class="button-container">
			<div class={animateIn(4, 'fade')}>
				<ButtonLink
					link="https://drive.google.com/file/d/1U6Z6PfnT-CBCUv4GbUzcyWh4jyzRKGO-/view?usp=share_link"
					iconLink="icons/resume.svg"
					text="Resume"
					type="primary"
				/>
			</div>
			<div class={animateIn(4, 'fade')}>
				<ButtonLink link="https://github.com/LipatJob" iconLink="icons/github.svg" text="Github" />
			</div>

			<div class={animateIn(4, 'fade')}>
				<ButtonLink
					link="https://www.linkedin.com/in/joblipat/"
					iconLink="icons/linkedin.png"
					text="LinkedIn"
				/>
			</div>

			<div class={animateIn(4, 'fade')}>
				<ButtonLink link="mailto:joblipat@gmail.com" iconLink="icons/email.svg" text="Email" />
			</div>
		</div>
	</div>
</div>

<style lang="scss">
	.section-container {
		margin: auto 0;
		padding-top: 100px;
		display: flex;
		flex-direction: column;
	}

	.section {
		display: flex;
		flex-direction: column;
		margin: auto;
	}

	.greeting {
		font-size: 64px;
		font-weight: 900;
		margin-bottom: 24px;
		@include md {
			font-size: 90px;
		}
		font-family: 'Roboto', sans-serif;
	}

	.greeting-name {
		color: $primary;
		font-size: 72px;
		font-family: 'Roboto', sans-serif;
		@include md {
			font-size: 118px;
		}
	}

	.greeting-name::before {
		content: '\A';
		white-space: pre;

		@include md {
			content: '';
			white-space: normal;
		}
	}

	.info {
		font-size: 26px;
		font-weight: 600;
		margin-bottom: 16px;
		@include md {
			font-size: 36px;
		}
	}

	.subinfo {
		font-size: 22px;
		color: $secondary;
		margin-bottom: 38px;
		@include md {
			line-height: 43px;
			font-size: 24px;
		}
	}

	.quote {
		font-style: italic;
	}

	.button-container {
		display: flex;
		flex-direction: row;
		gap: 10px;
		flex-wrap: wrap;
		justify-content: center;

		@include md {
			justify-content: left;
			gap: 24px;
		}
	}
</style>
