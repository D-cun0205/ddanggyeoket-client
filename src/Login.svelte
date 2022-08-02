<script>
    import { useNavigate, useLocation } from 'svelte-navigator';
    import { user } from './stores';
    import Textfield from '@smui/textfield';
    import '@smui/textfield/bare.css';
    import HelperText from '@smui/textfield/helper-text';
    import Button, { Label } from '@smui/button';
    import '@smui/button/bare.css';

    const navigate = useNavigate();
    const location = useLocation();

    let username = '';
    let password = '';

    function handleSubmit() {
        $user = { username, password };
        const from = ($location.state && $location.state.from) || "/";
        alert('from:' + from);
        navigate(from, { replace: true });
    }
</script>

<form on:submit={handleSubmit}>
    <div class="columns margins">
        <div>
            <Textfield
                bind:value={username}
                label="아이디"
                required 
            />
        </div>
        
        <div>
            <Textfield
                bind:value={password}
                type="password"
                label="비밀번호"
                required 
            />
        </div>
        <br />

        <Button
            color="secondary"
        >
            <Label>로그인</Label>
        </Button>

        <Button
        
        >
            <Label>회원가입</Label>
        </Button>

        <Button
        
        >
            <Label>비밀번호 초기화</Label>
        </Button>
    </div>
</form>