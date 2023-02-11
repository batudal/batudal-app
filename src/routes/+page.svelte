<script lang="ts">
	import { assets } from '$app/paths';

	let reach_link = 'https://twitter.com/takez0o';
	let skills = [
		{
			name: 'Ideation',
			description: 'Ideation; business modeling, strategy',
			icon: 'icons/idea.svg'
		},
		{
			name: 'Design',
			description: 'Design; branding,ui,ux',
			icon: 'icons/design.svg'
		},
		{
			name: 'Development',
			description: 'Fullstack development',
			icon: 'icons/development.svg'
		},
		{
			name: 'Soft Skills',
			description: 'Hiring, training, management',
			icon: 'icons/softskills.svg'
		}
	];
	let attempts = [
		{
			title: 'e-liner',
			success: false,
			description:
				'E-Liner builds upon the idea of a digital warehouse that solves the inefficiency problems in LTL transports. E-Liner is a software company modeled around a typical platform business; matching solo truck businesses with customers in need of cheap and fast cross-country transportation.',
			tags: [
				{
					title: 'HARD PIVOT 🐛',
					style: 'color: var(--color-pivot);'
				},
				{
					title: 'DEAD 💀',
					style: 'color: var(--color-primary);'
				}
			],
			achievements: [
				'Branding assets',
				'Routing algorithm POC',
				'Company formation',
				'Concierge bootstrap'
			],
			post_mortem:
				'Stakeholders had completely different visions for the product. It went unto being a hardware project for 5+ years, seeking a solution via hybrid-fuel technology for the transition period of truck transportation.'
		},
		{
			title: 'decoded labs',
			success: true,
			link: 'https://www.decoded-labs.com',
			description:
				'Decoded Labs is a developer collective committed to safeguard your ventures into the ambigous decentralized world.',
			tags: [
				{
					title: 'INCUBATING 👨‍🍼',
					style: 'color: var(--color-incubating);'
				}
			],
			achievements: ['Branding assets', 'Website, blog', 'First customers'],
			post_mortem:
				'Decoded Labs is still active and currently working on HonestWork; a freelancer marketplace for the decentralized web.'
		}
	];
</script>

<main>
	<div class="background-wrapper">
		<div class="background-container">
			<img src={`${assets}/takezo.png`} alt="takezo" />
		</div>
	</div>

	<div class="hero-container">
		<div class="content-container">
			<h1><span>Hi, </span>I'm Batu.</h1>
			<div style="height:24px" />
			<p>I'm an entrepreneur.</p>
			<div style="height:24px" />
			<p>I usually do all of these in a project;</p>
			<div style="height:12px" />
			{#each skills as skill}
				<div class="skills-container">
					<div class="skill">
						<img src={`${assets}/${skill.icon}`} alt={skill.name} />
						<div style="width:12px" />
						<p>{skill.description}</p>
					</div>
				</div>
			{/each}
			<div style="height:24px" />
			<p>And <span><strong>I fail a lot.</strong></span></p>
			<div style="height:24px" />
			<div class="status">
				<div class="tag">
					<h4><span>{attempts.length} </span>ATTEMPTS</h4>
				</div>
				<div style="width:20px" />
				<img src={`${assets}/icons/arrow.svg`} alt="arrow" />
				<div style="width:20px" />
				<div class="tag">
					<h4><span>{attempts.filter((a) => a.success == false).length} </span>FAILURES</h4>
				</div>
			</div>
			<div style="height:24px" />
			<p>Scroll to see my hall of shame.</p>
			<p>Feel free to <span><a href={reach_link}>reach out to me.</a></span></p>
		</div>
	</div>
	<div class="attempts-container">
		{#each attempts as attempt, i}
			<div class="card">
				<div class="card-header">
					<h2>{attempt.title}</h2>
					<div class="tags">
						{#each attempt.tags as tag, j}
							<div class="tag">
								<h4 style={tag.style}>{tag.title}</h4>
							</div>
							{#if j !== attempt.tags.length - 1}
								<div style="width:8px" />
							{/if}
						{/each}
					</div>
				</div>
				{#if attempt.link}
					<div style="height:12px" />
					<div class="tag-link">
						<h4>{attempt.link.split('www.')[1]}</h4>
					</div>
				{/if}
				<div style="height:48px" />
				<h3>ABSTRACT</h3>
				<div style="height:16px" />
				<p>{attempt.description}</p>
				<div style="height:48px" />
				<h3>PROGRESS</h3>
				<div style="height:16px" />
				{#each attempt.achievements as achievement}
					<div class="skills-container">
						<div class="skill">
							<img src={`${assets}/icons/check.svg`} alt="Achievements" />
							<div style="width:12px" />
							<p>{achievement}</p>
						</div>
					</div>
				{/each}
				<div style="height:48px" />
				<h3>POST-MORTEM</h3>
				<div style="height:16px" />
				<p>{attempt.post_mortem}</p>
			</div>
			{#if i !== attempts.length - 1}
				<div style="height:48px" />
			{/if}
		{/each}
	</div>
</main>

<style>
	main {
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.background-wrapper {
		position: fixed;
		top: 0;
		left: 0;
		width: 100vw;
		height: 100vh;
		z-index: -1;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.background-container {
		width: 920px;
		display: flex;
		flex-direction: row;
		justify-content: flex-end;
	}
	.background-container img {
		width: 100%;
		height: 800px;
		object-fit: scale-down;
		margin-right: -240px;
	}
	.hero-container {
		height: calc(100vh - 64px);
		width: 100vw;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	.content-container {
		width: 920px;
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
	}
	.skills-container {
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		align-items: flex-start;
		margin-left: 12px;
	}
	.skill {
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: center;
	}
	.status {
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: center;
	}
	.attempts-container {
		width: 100%;
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		align-items: center;
	}
	.card-header {
		width: 100%;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
	}
	.tags {
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: center;
	}
</style>
