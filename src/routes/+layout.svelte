<script lang="ts">
	import '$base/app.css';
	import Menu from 'lucide-svelte/icons/menu';
	import * as Avatar from '$base/lib/components/ui/avatar';
	import * as Sheet from '$lib/components/ui/sheet';
	import * as DropdownMenu from '$base/lib/components/ui/dropdown-menu';
	import { Button } from '$lib/components/ui/button';
	import { route } from '$base/lib/ROUTES';
	import { ModeWatcher } from 'mode-watcher';
	import { resetMode, setMode } from 'mode-watcher';
	import { Moon, Sun } from 'lucide-svelte';

	let { children } = $props();
</script>

<ModeWatcher />

<div class="flex min-h-screen w-full flex-col">
	<div class="sticky top-0 flex w-full">
		<div class="bg-fiesta_teal-foreground h-1 w-full"></div>
		<div class="bg-fiesta_fushcia-foreground h-1 w-full"></div>
		<div class="bg-fiesta_orange-foreground h-1 w-full"></div>
	</div>
	<header class="sticky top-0 flex h-16 items-center gap-4 border-b bg-black px-4 md:px-6">
		<nav
			class="hidden flex-col gap-6 text-lg font-medium md:flex md:flex-row md:items-center md:gap-5 md:text-sm lg:gap-6"
		>
			<Avatar.Root>
				<Avatar.Image src="/temp-sveltesa.jpeg" alt="@shadcn" />
				<Avatar.Fallback>Svelte SA</Avatar.Fallback>
			</Avatar.Root>
			<a
				href={route('/')}
				class="text-muted-foreground transition-colors hover:text-primary-foreground">Home</a
			>
			<a
				href={route('/blog')}
				class="text-muted-foreground transition-colors hover:text-primary-foreground"
			>
				Blog
			</a>
			<a
				href={route('/events')}
				class="text-muted-foreground transition-colors hover:text-primary-foreground">Events</a
			>
			<a
				href={route('/repl')}
				class="text-muted-foreground transition-colors hover:text-primary-foreground">REPL</a
			>
		</nav>
		<Sheet.Root>
			<Sheet.Trigger asChild let:builder>
				<div class="px-2">
					<Button variant="outline" size="icon" class="shrink-0 md:hidden" builders={[builder]}>
						<Menu class="h-5 w-5" />
						<span class="sr-only">Toggle navigation menu</span>
					</Button>
				</div>
			</Sheet.Trigger>
			<Sheet.Content side="left" class="bg-black">
				<div class="flex w-full">
					<div class="bg-fiesta_teal-foreground h-1 w-full"></div>
					<div class="bg-fiesta_fushcia-foreground h-1 w-full"></div>
					<div class="bg-fiesta_orange-foreground h-1 w-full"></div>
				</div>
				<nav class="flex flex-col gap-6 pt-4 text-lg font-medium">
					<div class="flex justify-between">
						<Avatar.Root>
							<Avatar.Image src="/temp-sveltesa.jpeg" alt="@shadcn" />
						</Avatar.Root>
						<DropdownMenu.Root>
							<DropdownMenu.Trigger asChild let:builder>
								<Button builders={[builder]} variant="outline" size="icon">
									<Sun
										class="h-[1.2rem] w-[1.2rem] rotate-0 scale-100 transition-all dark:-rotate-90 dark:scale-0"
									/>
									<Moon
										class="absolute h-[1.2rem] w-[1.2rem] rotate-90 scale-0 transition-all dark:rotate-0 dark:scale-100"
									/>
									<span class="sr-only">Toggle theme</span>
								</Button>
							</DropdownMenu.Trigger>
							<DropdownMenu.Content align="end">
								<DropdownMenu.Item on:click={() => setMode('light')}>Light</DropdownMenu.Item>
								<DropdownMenu.Item on:click={() => setMode('dark')}>Dark</DropdownMenu.Item>
								<DropdownMenu.Item on:click={() => resetMode()}>System</DropdownMenu.Item>
							</DropdownMenu.Content>
						</DropdownMenu.Root>
					</div>

					<a
						href={route('/')}
						class="text-muted-foreground transition-colors hover:text-primary-foreground">Home</a
					>
					<a
						href={route('/blog')}
						class="text-muted-foreground transition-colors hover:text-primary-foreground"
					>
						Blog
					</a>
					<a
						href={route('/events')}
						class="text-muted-foreground transition-colors hover:text-primary-foreground">Events</a
					>
					<a
						href={route('/repl')}
						class="text-muted-foreground transition-colors hover:text-primary-foreground">REPL</a
					>
				</nav>
			</Sheet.Content>
		</Sheet.Root>
		<div class="flex w-full items-center gap-4 md:ml-auto md:gap-2 lg:gap-4">
			<!-- * Search input if needed -->
			<!-- <form class="ml-auto flex-1 sm:flex-initial">
				<div class="relative">
					<Search class="absolute left-2.5 top-2.5 h-4 w-4 text-muted-foreground" />
					<Input
						type="search"
						placeholder="Search blog"
						class="pl-8 sm:w-[300px] md:w-[200px] lg:w-[300px]"
					/>
				</div>
			</form> -->

			<!-- TODO: User Profiles -->
			<!-- <DropdownMenu.Root>
        <DropdownMenu.Trigger asChild let:builder>
          <Button builders={[builder]} variant="secondary" size="icon" class="rounded-full">
            <Sun
              class="h-[1.2rem] w-[1.2rem] rotate-0 scale-100 transition-all dark:-rotate-90 dark:scale-0"
            />
            <span class="sr-only">Toggle user menu</span>
          </Button>
        </DropdownMenu.Trigger>
        <DropdownMenu.Content align="end">
          <DropdownMenu.Label>My Account</DropdownMenu.Label>
          <DropdownMenu.Separator />
          <DropdownMenu.Item>Settings</DropdownMenu.Item>
          <DropdownMenu.Item>Support</DropdownMenu.Item>
          <DropdownMenu.Separator />
          <DropdownMenu.Item>Logout</DropdownMenu.Item>
        </DropdownMenu.Content>
      </DropdownMenu.Root> -->
			<div class="ml-auto">
				<DropdownMenu.Root>
					<DropdownMenu.Trigger asChild let:builder>
						<Button builders={[builder]} variant="outline" size="icon">
							<Sun
								class="h-[1.2rem] w-[1.2rem] rotate-0 scale-100 transition-all dark:-rotate-90 dark:scale-0"
							/>
							<Moon
								class="absolute h-[1.2rem] w-[1.2rem] rotate-90 scale-0 transition-all dark:rotate-0 dark:scale-100"
							/>
							<span class="sr-only">Toggle theme</span>
						</Button>
					</DropdownMenu.Trigger>
					<DropdownMenu.Content align="end">
						<DropdownMenu.Item on:click={() => setMode('light')}>Light</DropdownMenu.Item>
						<DropdownMenu.Item on:click={() => setMode('dark')}>Dark</DropdownMenu.Item>
						<DropdownMenu.Item on:click={() => resetMode()}>System</DropdownMenu.Item>
					</DropdownMenu.Content>
				</DropdownMenu.Root>
			</div>
		</div>
	</header>
	<main class="flex flex-1 flex-col gap-4 p-4 md:gap-8 md:p-8">
		{@render children()}
	</main>
</div>
