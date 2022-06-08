<script>
    import { useNavigate, useLocation } from "svelte-navigator";
    import { user } from "./stores";

    const navigate = useNavigate();
    const location = useLocation();

    let username;
    let password;

    function handleSubmit() {
        $user = { username, password };
        const from = ($location.state && $location.state.from) || "/";
        alert('from:' + from);
        navigate(from, { replace: true });
    }
</script>

<h3>Login</h3>
<form on:submit={handleSubmit}>
    <input
        bind:value={username}
        type="text"
        name="username"
        placeholder="write username"
    />
    <br />
    <input
        bind:value={password}
        type="password"
        name="password"
        placeholder="write password"
    />
    <br />
    <button type="submit">Login</button>
</form>