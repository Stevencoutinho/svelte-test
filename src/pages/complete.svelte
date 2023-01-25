<script lang="ts">
  import { Link, useLocation, useNavigate } from "svelte-navigator";

  const location = useLocation();
  const navigate = useNavigate();
  let nickname = "";
  let emissions = 0;

  $: {
    const params = Object.fromEntries(new URLSearchParams($location.search).entries());
    if (!params.emissions && isNaN(Number(params.emissions)) && Number(params.emissions)) {
      navigate("/");
    } else {
      nickname = params.nickname;
      emissions = Number(params.emissions);
    }

  };
</script>

<main>
  {#if nickname}
    <p>{nickname}様</p>
  {/if}
  <p>支払いが完了しました！</p>
  <p>{emissions}kg-CO<sub>2</sub></p>
  <Link to={`/users?nickname=${nickname}&emissions=${emissions}`}>応援者リストを見る</Link>
</main>