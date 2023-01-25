<script lang="ts">
  import { Router, Route } from "svelte-navigator";
  import Home from "./pages/index.svelte";
  import Complete from "./pages/complete.svelte";
  import Users from "./pages/users.svelte";
</script>

<Router>
  <Route path="/" component={Home} />
  <Route path="/complete" component={Complete} />
  <Route path="/users" component={Users} />
</Router>