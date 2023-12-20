<script lang="ts">
  import Navbar from "./components/navbar.svelte";
  import Login from "./components/login.svelte";
  import UserList from "./components/userList.svelte";
</script>

<main class="w-screen max-h-screen max-w-screen h-screen flex-row">
  <Navbar />
  <div class="container m-auto h-full bg-base-200 rounded-none sm:rounded-2xl">
    <!-- <Login /> -->
    <UserList userId={123} qrKey={123} userName={'Prashant'}/>
  </div>
</main>