<template>
    <div class="min-h-screen flex flex-col">
        <!-- Header -->
        <header class="bg-green-600 text-white shadow-md">
            <nav class="container mx-auto flex justify-between items-center py-3 ">
                <div class="flex space-x-4">
                    <a href="/" class="text-md font-semibold hover:underline">Home</a>
                    <a href="/about" class="text-md font-semibold hover:underline">About</a>
                </div>
            </nav>
        </header>

        <!-- Main Content -->
        <main class="flex-grow container mx-auto py-2 ">
            <slot />
        </main>
    </div>
</template>
