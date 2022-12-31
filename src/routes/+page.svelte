<script lang="ts">
	import { page } from '$app/stores';
	import f from '$env/static/public';
	import { supabase } from '$lib/supabaseClient';

	const getURL = () => {
		console.log(f);

		let url =
			f.PUBLIC_SITE_URL ?? // Set this to your site URL in production env.
			f.PUBLIC_VERCEL_URL ?? // Automatically set by Vercel.
			'http://localhost:4173/';
		// Make sure to include `https://` when not localhost.
		url = url.includes('http') ? url : `https://${url}`;
		// Make sure to including trailing `/`.
		url = url.charAt(url.length - 1) === '/' ? url : `${url}/`;

		console.log(url);
		return url;
	};

	const signInWithDiscord = async () => {
		try {
			console.log(window.location.origin);
			const { data, error } = await supabase.auth.signInWithOAuth({
				provider: 'discord',
				options: {
					redirectTo: getURL()
				}
			});
		} catch (error) {
			if (error instanceof Error) {
				alert(error.message);
			}
		}
	};

	const signOut = async () => {
		const { error } = await supabase.auth.signOut();
	};

	let username: string | null = null;
	let website: string | null = null;
	let avatarUrl: string | null = null;

	const getProfile = async () => {
		try {
			const { user } = $page.data.session;

			const { data, error, status } = await supabase
				.from('profiles')
				.select(`display_name, avatar_url`)
				.eq('id', user.id)
				.single();

			if (data) {
				console.log(data);
			}

			if (error && status !== 406) throw error;
		} catch (error) {
			if (error instanceof Error) {
				alert(error.message);
			}
		}
	};

	async function updateProfile() {
		try {
			const { user } = $page.data.session;

			const updates = {
				id: user.id,
				wb_id: 'Torbaz'
			};

			let { error } = await supabase.from('profiles').upsert(updates);

			if (error) throw error;
		} catch (error) {
			if (error instanceof Error) {
				alert(error.message);
			}
		}
	}
</script>

<div class="hero min-h-screen" style="background-image: url('../spacejam.jpg');">
	<div class="hero-overlay bg-opacity-0" />
	<div class="hero-content text-center text-neutral-content -mt-20">
		<div class="navbar bg-base-100">
			<div class="flex-1">
				<a class="btn btn-ghost normal-case text-xl top-left">
					<img src="../multiversusocetransparent.png" alt="Multiversus OCE logo" />
				</a>
			</div>
			<div class="flex-none">
				<ul class="menu menu-horizontal px-1">
					<li>
						<a
							href="https://twitter.com/multiversus_oce"
							target="_blank"
							class="text-blue-300 font-bold">Twitter</a
						>
					</li>
					<li>
						<a
							href="https://www.twitch.tv/multiversus_oce"
							target="_blank"
							class="text-purple-500 font-bold">Twitch</a
						>
					</li>
					<li>
						<a
							href="https://www.start.gg/user/b53ca12b"
							target="_blank"
							class="text-red-500 font-bold">start.gg</a
						>
					</li>
					<li>
						{#if !$page.data.session}
							<div class="flex-center">
								<button type="button" class="btn btn-primary" on:click={signInWithDiscord}
									>Sign in with Discord</button
								>
							</div>
						{:else if $page.data.session}
							<form class="flex-center">
								<div>
									<button class="button block" style="color: white" on:click={signOut}
										>Sign Out</button
									>
								</div>
							</form>
						{/if}
					</li>
				</ul>
			</div>
		</div>
		<div class="max-w-2xl">
			<h1 class="mb-5 text-6xl font-bold text-white">Join MultiVersus OCE</h1>
			<h2 class="mb-5 text-2xl font-bold">
				We host weekly tournaments. Join our friendly, active community today!
			</h2>
			<p class="mb-5" />
			<a href="https://discord.gg/mvsoce" target="_blank" class="btn btn-primary">MVSOCE Discord</a>
			<button type="button" class="btn btn-primary" on:click={getProfile}>Test Button</button>
			<button type="button" class="btn btn-primary" on:click={updateProfile}>L + Ratio</button>
		</div>
	</div>
</div>
<div class="disclaimer p-4 text-center text-neutral-300 font-light">
	<p>Please note: We are not an official entity or affiliated with MultiVersus in any capacity</p>
</div>

<style>
	.navbar {
		position: fixed; /* Fixes the navbar to the top of the page */
		top: 0; /* Positions the navbar at the top of the page */
		left: 0; /* Positions the navbar at the left side of the page */
		right: 0; /* Takes up the full width of the page */
		z-index: 1; /* Ensures that the navbar is displayed above other elements on the page */
		background-color: transparent;
	}
	a.top-left {
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		z-index: 2;
		width: 10%;
		height: 10%;
	}
</style>
