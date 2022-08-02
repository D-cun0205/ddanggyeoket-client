<script>
	import { Router, Route, Link } from 'svelte-navigator';
	import Login from "./Login.svelte";
	import PrivateRoute from "./PrivateRoute.svelte";
	import { user } from './stores.js';

	function handleLogout() {
		$user = null;
	}
</script>

<Router>
	<header>
		<h1>땅겨켓</h1>
	</header>

	<nav>
		<Link to="/">Home</Link>
		<Link to="about">About</Link>
		<Link to="profile">Profile</Link>
	</nav>

	<main>
		<Route path="login">
			<Login />
		</Route>

		<Route path="/">
			<h3>Home</h3>
			<p>home...</p>
		</Route>

		<Route path="about">
			<h3>About</h3>
			<p>about...</p>
		</Route>

		<PrivateRoute path="profile" let:location>
			<h3>Welcome {$user.username}</h3>
			<button on:click={handleLogout}>Logout</button>
		</PrivateRoute>
	</main>
</Router>