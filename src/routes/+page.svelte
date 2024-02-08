<script>
	import education from '$lib/education.js';
	import experience from '$lib/experience.js';
	import certificates from '$lib/certificates.js';
	import projects from '$lib/projects.js';
	import skils from '$lib/skils.js';
	import ChevronRight from 'virtual:icons/mdi/chevron-right';
	import Linkedin from 'virtual:icons/mdi/linkedin';
	import Github from 'virtual:icons/mdi/github';
	import Link from 'virtual:icons/mdi/link';
	import Intro from './Intro.svelte';

	let links = {
		linkedin: 'https://www.linkedin.com/in/juan-francisco-araujo-bayas-57b170126/',
		github: 'https://github.com/juan15-fran'
	};

	let languages = ['Spanish (native)', 'English (fluent)', 'French (fluent)'];

	let showExperience = true;
	let showEducation = true;
	let showSkills = true;
	let showProjects = true;
</script>

<div class="m-auto p-4 space-y-4 sm:grid sm:grid-cols-7 gap-4 items-start py-32">
	<Intro class="sm:hidden" />
	<section class="flex flex-col gap-4 rounded-md bg-stone-100 p-4 col-span-1 col-start-2 shrink-0">
		<img
			src="profile-img.jpeg"
			alt="Profile Picture"
			class="rounded-lg m-auto"
			aria-hidden="true"
		/>
		<div class="flex gap-2">
			<a href={links.linkedin} target="_blank" rel="noopener noreferrer" class="w-fit"
				><Linkedin class="h-10 w-10 text-sky-500" />
			</a>
			<a href={links.github} target="_blank" rel="noopener noreferrer" class="w-fit"
				><Github class="h-10 w-10 text-black" />
			</a>
		</div>

		<!-- Languages -->
		<div>
			<h2 class="text-2xl font-semibold mb-2">Languages</h2>
			<div class="flex flex-wrap gap-1">
				{#each languages as language}
					<span
						class="bg-white rounded-full px-2 py-1 text-sm text-stone-500 hover:text-black font-semibold"
						>{language}</span
					>
				{/each}
			</div>
		</div>

		<!-- Certificates -->
		<div>
			<h2 class="text-2xl font-semibold mb-2">Certifications</h2>
			<div class="flex flex-wrap gap-1">
				{#each certificates as certificate}
					<span
						class="bg-white rounded-full px-2 py-1 text-sm text-stone-500 hover:text-black font-semibold"
						>{certificate}</span
					>
				{/each}
			</div>
		</div>

		<!-- Projects -->
		<section>
			<button
				on:click={() => (showProjects = !showProjects)}
				class="text-3xl font-semibold mb-2 hover:text-stone-400 flex items-center gap-2"
			>
				{#if showProjects}
					<ChevronRight class="w-8 h-8 transform rotate-90" />
				{:else}
					<ChevronRight class="w-8 h-8" />
				{/if}
				<span>Projects</span>
			</button>
			{#if showProjects}
				<div class="flex flex-wrap gap-4">
					{#each projects as project}
						<a
							href={project.link}
							target="_blank"
							rel="noopener noreferrer"
							class="text-stone-500 border p-2 hover:bg-stone-200 bg-white rounded-lg"
						>
							<h3>{project.title} <Link class="h-5 w-5 text-sky-500" /></h3>
							<p class="text-lg font-bold text-stone-500">
								<span class="italic text-stone-400 mr-2">at</span>{project.company}
							</p>
							<p class="italic text-stone-500 shrink-0">{project.duration}</p>
						</a>
					{/each}
				</div>
			{/if}
		</section>
	</section>
	<div class="flex flex-col gap-8 w-full col-span-4">
		<Intro class="hidden sm:block" />

		<!-- Experiencs -->
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
							<div class="w-full">
								<h2>{job.title}</h2>
								<div class="flex mb-3 flex-col lg:flex-row justify-between gap-2 border-b">
									<p class="text-lg font-bold text-stone-500">
										<span class="italic text-stone-400 mr-2">at</span>{job.company}
									</p>
									<p class="italic text-stone-500 shrink-0">{job.duration}</p>
								</div>
								<p>{job.description}</p>
							</div>
						</li>
					{/each}
				</ul>
			{/if}
		</section>

		<!-- Education -->
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
								<div>
									<h2>{school.subtitle}</h2>
									<div class="flex flex-col lg:flex-row justify-between gap-2 border-b">
										<div>
											<p class="text-lg font-bold text-stone-500">
												<span class="italic text-stone-400 mr-2">at</span>{school.title}
											</p>
											{#if school.grade}
												<p class="text-lg font-bold text-stone-500">
													<span class="italic text-stone-400 mr-2">with</span>{school.grade}
												</p>
											{/if}
										</div>
										<p class="italic text-stone-500 shrink-0">{school.duration}</p>
									</div>
								</div>
								<p>{school.skills}</p>
							</div>
						</li>
					{/each}
				</ul>
			{/if}
		</section>

		<!-- Skils -->
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
					{#each skils as skill}
						<li>
							<h2>{skill.title}</h2>
							<div class="flex flex-wrap gap-2">
								{#each skill.items as item}
									<span class="bg-white rounded-full px-2 py-1">{item}</span>
								{/each}
							</div>
						</li>
					{/each}
				</ul>
			{/if}
		</section>
	</div>
</div>
