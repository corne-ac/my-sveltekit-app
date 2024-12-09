<script>
	import '../app.css';
	let { children } = $props();
</script>
<!-- navbar container -->
<div class="navbar"> 

	<div class="navbar-start">
		<div class=" hover:text-blue-500">
			<svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
			  <path d="M3 9l9-7 9 7"></path>
			  <path d="M9 22V12h6v10"></path>
			</svg>
		  </div>
	</div>

	<div class="navbar-center">
		<ul class="menu menu-horizontal px-1 font-bold ">
			<li><a href="/about" class="hover:font-extrabold">about</a></li>
			<li><a href="/">item 1</a></li>
			<li><a href="/">item 1</a></li>
			<li><a href="/">item 1</a></li>
		</ul>
	</div>

	<div class="navbar-end">
		<a>item</a>
	</div>

</div>

{@render children()}
