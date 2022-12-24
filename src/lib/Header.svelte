<script>
  import logo from "../assets/icons8-todo-list-50.png";
  import github from "../assets/icons8-github-48.png";
  import { Link } from "svelte-navigator";
</script>

<header>
  <div class="corner">
    <a href="/">
      <img src={logo} alt="STodoList" />
    </a>
  </div>

  <nav>
    <ul>
      <li aria-current="page">
        <Link to="/signup"><span>SignUp</span></Link>
      </li>
      <li aria-current="page">
        <Link to="/login"><span>Login</span></Link>
      </li>
      <li aria-current="page">
        <a href="https://github.com/sveltejs/kit">
          <img src={github} alt="GitHub" />
        </a>
      </li>
    </ul>
  </nav>


</header>

<style>
  header {
    margin: -10px;
    display: flex;
    justify-content: space-between;
    background-color: white;
  }

  .corner {
    width: 3em;
    height: 3em;
  }

  .corner a, li a {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100%;
  }

  .corner img, li img {
    width: 2em;
    height: 2em;
    object-fit: contain;
  }

  nav {
    display: flex;
    justify-content: center;
    --background: white;
  }
  ul {
    position: relative;
    padding: 0;
    margin: 0 0 0 20px;
    height: 3em;
    display: flex;
    justify-content: space-between;
    align-items: center;
    list-style: none;
    background: var(--background);
    background-size: contain;
  }

  li {
    position: relative;
    height: 100%;
  }
  li span {
    display: flex;
    height: 100%;
    align-items: center;
    text-decoration: none;
    margin-right: 8px;
    margin-left: 4px;
    color: black;
    font-weight: 500;
    font-size: 1rem;
    transition: color 0.2s linear;
  }

  li span:hover {
    color: var(--color-theme-1);
  }
</style>
