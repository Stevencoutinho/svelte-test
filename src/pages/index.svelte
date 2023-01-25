<script lang="ts">
  import { useNavigate } from "svelte-navigator";

  const navigate = useNavigate();
  let emissions = 7;
  let nickname = "";

  const handleSubmit = () => {
    const params = new URLSearchParams({
      nickname: nickname,
      emissions: emissions.toString(),
    });
    navigate(`/complete?${params}`);
    return;
  };
</script>

<main>
  <form on:submit|preventDefault={handleSubmit}>
    <div class="price-select-container">
      <p>金額を選択</p>
      <dl class="price-select">
        <div>
          <dt>7kg-CO<sub>2</sub></dt>
          <dd><label>
            <input type="radio" bind:group={emissions} name="emissions" value={7} />¥100</label></dd>
        </div>
        <div>
          <dt>35kg-CO<sub>2</sub></dt>
          <dd><label><input type="radio" bind:group={emissions} name="emissions" value={35} />¥500</label></dd>
        </div>
        <div>
          <dt>70kg-CO<sub>2</sub></dt>
          <dd><label><input type="radio" bind:group={emissions} name="emissions" value={70} />¥700</label></dd>
        </div>
      </dl>
    </div>
    <div>
      <p>ニックネームを入力: <input type="text" bind:value={nickname} /></p>
    </div>
    <p><button type="submit">オフセットする</button></p>
  </form>
</main>


<style>
main {
  padding: 10px;
}

.price-select-container {
  width: 100%;
}

.price-select div {
  display: flex;
}
</style>