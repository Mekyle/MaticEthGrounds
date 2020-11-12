<script>
  import { Router, Route, Link } from "svelte-routing";
  import Home from "./public/pages/Home.svelte";
  import About from "./public/pages/About.svelte";
  export let url = ""; //This property is necessary declare to avoid ignore the Router

  import Button from "./public/components/Button.svelte";
  import Navbar from "./public/components/Navbar.svelte";
  import Test from "./public/components/Test.svelte";
</script>

<style>
  main {
    font-family: sans-serif;
    text-align: center;
  }
</style>

<main>
  <Router url="{url}">
 <nav>
    <Link to="/">Home</Link>
    <Link to="about">About</Link>
  </nav>S
  <div>
    <Route path="about" component="{About}" /> 
    <!--for now the router just support case sensitive,
        one workaround colud be add two time the route
        Example.
       <Route path="About" component="{About}" /> 
    -->
    <Route path="/"><Home /></Route>
  </div>
</Router>
  <Test />
</main>