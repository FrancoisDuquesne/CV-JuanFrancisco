<script>
	import education from '$lib/education.js';
	import experience from '$lib/experience.js';
	import ChevronRight from 'virtual:icons/mdi/chevron-right';
	import Linkedin from 'virtual:icons/mdi/linkedin';

	let info = {
		name: 'Juan Francisco',
		surname: 'Araujo Bayas',
		email: 'juanfran@live.com',
		phone: '123-456-7890',
		linkedin: 'https://www.linkedin.com/in/juan-francisco-araujo-bayas-57b170126/'
	};

	let showExperience = true;
	let showEducation = true;
	let showSkills = true;
</script>

<div class="m-auto items-center md:max-w-7xl p-4 md:p-10">
	<div
		class="flex flex-col md:flex-row relative items-start gap-12 md:gap-4 w-full md:divide-x divide-stone-300"
	>
		<section
			class="w-full md:max-w-sm md:w-fit md:fixed md:-translate-x-full md:pr-4 shrink-0 flex flex-col gap-4 rounded-md bg-stone-100 md:bg-transparent p-4"
		>
			<div class="w-full">
				<img
					src="profile-img.jpeg"
					alt="Profile Picture"
					class="w-52 h-52 rounded-lg m-auto"
					aria-hidden="true"
				/>
			</div>
			<h1>{info.name} <br /> {info.surname}</h1>

			<div class="flex flex-col gap-2">
				<p>
					<span class="text-stone-500">mail:</span>
					<a href="mailto:{info.email}">{info.email}</a>
				</p>
				<p><span class="text-stone-500">tel:</span> {info.phone}</p>
				<a href={info.linkedin} target="_blank" rel="noopener noreferrer" class="w-fit"
					><Linkedin class="h-10 w-10" />
				</a>
			</div>
		</section>

		<div class="flex flex-col gap-8 w-full md:pl-4">
			<section>
				<button
					on:click={() => (showExperience = !showExperience)}
					class="text-3xl font-semibold mb-2 hover:text-stone-400 flex items-center gap-2"
				>
					{#if showExperience}
						<ChevronRight class="w-8 h-8 transform rotate-90" />
					{:else}
						<ChevronRight class="w-8 h-8" />
					{/if}
					<span>Experience</span>
				</button>
				{#if showExperience}
					<ul class="list">
						{#each experience as job}
							<li>
								<img src={job.img} alt={job.company} class="w-20 h-20 rounded-lg" />
								<div class="w-full space-y-3">
									<div class="flex flex-col md:flex-row items-end justify-between gap-2 border-b">
										<div>
											<h2>{job.title}</h2>
											<p class="text-lg font-bold text-stone-500">
												<span class="italic text-stone-400 mr-2">at</span>{job.company}
											</p>
										</div>
										<p class="italic text-stone-500 shrink-0">{job.duration}</p>
									</div>
									<p>{job.description}</p>
								</div>
							</li>
						{/each}
					</ul>
				{/if}
			</section>

			<section>
				<button
					on:click={() => (showEducation = !showEducation)}
					class="text-3xl font-semibold mb-2 hover:text-stone-400 flex items-center gap-2"
				>
					{#if showEducation}
						<ChevronRight class="w-8 h-8 transform rotate-90" />
					{:else}
						<ChevronRight class="w-8 h-8" />
					{/if}
					<span>Education</span>
				</button>

				{#if showEducation}
					<ul class="list">
						{#each education as school}
							<li>
								<img src={school.img} alt={school.title} class="w-20 h-20 rounded-lg" />
								<div class="w-full space-y-3">
									<div class="flex flex-col md:flex-row items-end justify-between gap-2 border-b">
										<div>
											<h2>{school.subtitle}</h2>
											{#if school.grade}
												<p class="text-lg font-bold text-stone-500">
													<span class="italic text-stone-400 mr-2">with</span>{school.grade}
												</p>
											{/if}
											<p class="text-lg font-bold text-stone-500">
												<span class="italic text-stone-400 mr-2">at</span>{school.title}
											</p>
										</div>
										<p class="italic text-stone-500 shrink-0">{school.duration}</p>
									</div>
									<p>{school.skills}</p>
								</div>
							</li>
						{/each}
					</ul>
				{/if}
			</section>

			<section>
				<button
					on:click={() => (showSkills = !showSkills)}
					class="text-3xl font-semibold mb-2 hover:text-stone-400 flex items-center gap-2"
				>
					{#if showSkills}
						<ChevronRight class="w-8 h-8 transform rotate-90" />
					{:else}
						<ChevronRight class="w-8 h-8" />
					{/if}
					<span>Skills</span>
				</button>
				{#if showSkills}
					<ul class="list">
						<li>
							<h2>Frontend</h2>
							<p>HTML, CSS, JavaScript, Svelte, React, Vue, TailwindCSS, Bootstrap</p>
						</li>
						<li>
							<h2>Backend</h2>
							<p>Node.js, Express, MongoDB, MySQL, PostgreSQL, Firebase, GraphQL, REST</p>
						</li>
						<li>
							<h2>Tools</h2>
							<p>Git, GitHub, GitLab, Bitbucket, Jira, Trello, Slack, Discord, Zoom, Google Meet</p>
						</li>
						<li>
							<h2>Other</h2>
							<p>
								Agile, Scrum, Kanban, CI/CD, Docker, Kubernetes, AWS, Azure, GCP, Heroku, Netlify,
								Vercel
							</p>
						</li>
					</ul>
				{/if}
			</section>
		</div>
	</div>
</div>
