<!-- App.svelte -->

<script>
// @ts-nocheck

  import "./app.css";
  import { Info } from 'lucide-svelte';
  import { Button, buttonVariants } from "$lib/components/ui/button/index.js";
  import * as Accordion from "$lib/components/ui/accordion/index.js";
  import * as Card from "$lib/components/ui/card/index.js";
  import * as Select from "$lib/components/ui/select/index.js";
  import { Input } from "$lib/components/ui/input/index.js";
  import { Label } from "$lib/components/ui/label/index.js";
  import * as Tabs from "$lib/components/ui/tabs/index.js";
  import * as Table from "$lib/components/ui/table/index.js";
  import * as Tooltip from "$lib/components/ui/tooltip/index.js";
  import { ScrollArea } from "$lib/components/ui/scroll-area/index.js";
  import { Toaster } from "$lib/components/ui/sonner/index.js"
  import { toast } from "svelte-sonner";
  import * as Popover from "$lib/components/ui/popover/index.js";
  

  let currentPage = 'home';
  let filterGenre = '';
  let filterLanguage = '';

  let popularSongs = [
    {
      icon: 'https://i.scdn.co/image/ab67616d0000b273283a117f2bc39bc4122692c0',
      name: 'Shoka',
      artist: 'Ado',
    },
    {
      icon: 'https://i.scdn.co/image/ab67616d0000b273b7982c8970577920c74d601e',
      name: 'NOX LUX',
      artist: 'MYTH & ROID',
    },
    {
      icon: 'https://i.scdn.co/image/ab67616d0000b273e204aafb5c393179c77c5253',
      name: 'Show',
      artist: 'Ado',
    },
  ];
  
  let trendingSongs = [
    {
      icon: 'https://i.scdn.co/image/ab67616d0000b27336032cb4acd9df050bc2e197',
      name: 'APT.',
      artist: 'ROSE, Bruno Mars',
    },
    {
      icon: 'https://i.scdn.co/image/ab67616d0000b2731dac3694b3289cd903cb3acf',
      name: "That's So True",
      artist: 'Gracie Abrams',
    },
    {
      icon: 'https://i.scdn.co/image/ab67616d00001e02d9985092cd88bffd97653b58',
      name: 'luther (with sza)',
      artist: 'Kendrick Lamar, SZA',
    },
  ];

  let indieSongs = [
    {
      icon: 'https://i.scdn.co/image/ab67616d0000b273f8d014e705472544d67edcbb',
      name: "would've been you",
      artist: 'sombr',
    },
    {
      icon: 'https://m.media-amazon.com/images/I/51Gz2YRDkTL._UXNaN_FMjpg_QL85_.jpg',
      name: 'Hollow',
      artist: 'Diives',
    },
    {
      icon: 'https://cdn-images.dzcdn.net/images/cover/01efec6c9f8262be94bdeec19247aa41/0x1900-000000-80-0-0.jpg',
      name: 'Dylan',
      artist: 'Deyaz',
    },
  ];

  let savedItems = [
    "https://open.spotify.com/embed/track/7MJgZqsnLjhGwcZpRuHyp0?utm_source=generator&theme=0",
    "https://open.spotify.com/embed/track/0h9HqYMU1EGRZ8E3aQ2lJE?utm_source=generator&theme=0",
    "https://open.spotify.com/embed/artist/7to1UlTpu40h7CpjRPkGqA?utm_source=generator&theme=0",
    "https://open.spotify.com/embed/track/4lriIG2vNqwDWzOj2I9rtj?utm_source=generator&theme=0"
  ];

  let randomSongs = {
    'Rock': {
      'English': 'https://open.spotify.com/embed/track/24l3mfIPWVa645a9LEwSHx?utm_source=generator&theme=0',
      'Japanese': 'https://open.spotify.com/embed/track/6xXbvCVJJvDASAmKGE3IXh?utm_source=generator&theme=0'
    },
    'Pop': {
      'English': 'https://open.spotify.com/embed/track/2aL4lMGhWdPpyPL6COPou7?utm_source=generator&theme=0',
      'Japanese': 'https://open.spotify.com/embed/track/3lsd1CbDC5ejAOJhPn5dB9?utm_source=generator&theme=0'
    },
  }

  let randomArtists = {
    'Rock': {
      'English': 'https://open.spotify.com/embed/artist/3N8Hy6xQnQv1F1XCiyGQqA?utm_source=generator&theme=0',
      'Japanese': 'https://open.spotify.com/embed/artist/630wzNP2OL7fl4Xl0GnMWq?utm_source=generator&theme=0'
    },
    'Pop': {
      'English': 'https://open.spotify.com/embed/artist/06HL4z0CvFAxyc27GXpf02?utm_source=generator&theme=0',
      'Japanese': 'https://open.spotify.com/embed/artist/6bDWAcdtVR3WHz2xtiIPUi?utm_source=generator&theme=0'
    },
  }

</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Tangerine:wght@400;700&display=swap');
  .horizon {
  font-family: "Tangerine", cursive;
  font-weight: 700;
  font-style: normal;
}


  main {
    background:linear-gradient(60deg, #1db954, #191414);
  }

  #header {
    background-color: #191414;
  }

  .invert { filter: invert(100%); }

  .header-link {
    transition: all 0.4s;
    position: relative;
    cursor: pointer;
  }

  .header-link::after {
    content: '';
    height: 2px;
    width: 100%;
    background: #1db954;
    position: absolute;
    left: 0;
    bottom: -1px;
    opacity: 0;
  }

  .header-link:hover::after {
    opacity: 1;
  }
</style>

<main class="h-full w-full">
  <Toaster />

  {#if currentPage == 'home'}
  <div id="main" class="h-full">
    <div class="text-center">
      <div class="flex text-center justify-center">
        <p class="pt-56 text-white text-7xl font-bold ml-32 horizon">Horizon</p>
        <img src="https://freesvg.org/img/corbeau_Eighth_note.png" alt="Eighth Note" class="size-36 mt-32" />
      </div>
      <p class="text-white text-xl pb-10">Discover new horizons of music</p>
      <div class="flex items-center justify-center gap-4">
        <p class="text-white text-lg ml-[-11.5%]">Discover a random: </p>
        <Button variant="hero" class="w-28" on:click={() => currentPage = 'song'}>Song</Button>
        <Button variant="hero" class="w-28" on:click={() => currentPage = 'song'}>Artist</Button>

        <Popover.Root>
          <Popover.Trigger class={buttonVariants({variant: "secondary"})}>Filters</Popover.Trigger>
          <Popover.Content class="w-80">
            <div class="grid gap-4">
              <div class="space-y-2">
                <h4 class="font-medium leading-none">Filters</h4>
                <p class="text-muted-foreground text-sm">
                  Specify the genre and language of today's random song and artist.
                </p>
              </div>
              <div class="grid gap-2">
                <div class="grid grid-cols-3 items-center gap-4">
                  <Label for="genre">Genre</Label>
                  <Select.Root type="single" id="genre" bind:value={filterGenre}>
                    <Select.Trigger class="w-[180px]">{filterGenre == '' ? 'Select a genre' : filterGenre}</Select.Trigger>
                    <Select.Content>
                      <Select.Item value="Rock">Rock</Select.Item>
                      <Select.Item value="Pop">Pop</Select.Item>
                    </Select.Content>
                  </Select.Root>
                </div>
                <div class="grid grid-cols-3 items-center gap-4">
                  <Label for="language">Language</Label>
                  <Select.Root type="single" id="language" bind:value={filterLanguage}>
                    <Select.Trigger class="w-[180px]">{filterLanguage == '' ? 'Select a language' : filterLanguage}</Select.Trigger>
                    <Select.Content>
                      <Select.Item value="English">English</Select.Item>
                      <Select.Item value="Japanese">Japanese</Select.Item>
                    </Select.Content>
                  </Select.Root>
                </div>
              </div>
            </div>
          </Popover.Content>
        </Popover.Root>
      </div>

      <div class="flex justify-center text-white mt-8">
        <Accordion.Root type="single" class="w-1/2">
          <Accordion.Item value="item-1">
            <Accordion.Trigger>How does it work?</Accordion.Trigger>
            <Accordion.Content>
              Horizon chooses a fully RANDOM song or artist based on your selections and filters. Break out of the algorithms
              created by other music services and take this chance to uncover hidden gems!
            </Accordion.Content>
          </Accordion.Item>
          <Accordion.Item value="item-2">
            <Accordion.Trigger>How often can I see new selections?</Accordion.Trigger>
            <Accordion.Content>
              Every day there will be a new random song and artist of the day for you to view! But by customizing
              your filters, you can potentially see multiple songs and artists per day.
            </Accordion.Content>
          </Accordion.Item>
          <Accordion.Item value="item-3">
            <Accordion.Trigger>What if I see something I like?</Accordion.Trigger>
            <Accordion.Content>
              If you don't have a Spotify account to immediately save it with, you can use the save button and access
              it from the 'Saved' page so that you won't lose it even once a new day begins.
            </Accordion.Content>
          </Accordion.Item>
        </Accordion.Root>
      </div>
      
      
    </div>
  </div>
    
  {:else if currentPage == 'song' || currentPage == 'artist' || currentPage == 'saved'}
    <div id="random" class="w-full">
      <!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
      <div id="header" class="flex text-xl p-2 text-white fixed w-full">
        <!-- svelte-ignore a11y_no_static_element_interactions -->
        <!-- svelte-ignore a11y_click_events_have_key_events -->
        <div class="flex cursor-pointer" on:click={() => {currentPage = 'home'}}>
          <p class="ml-2 horizon text-3xl">Horizon</p>
          <img src="https://freesvg.org/img/corbeau_Eighth_note.png" alt="Eighth Note" class="ml-1 size-6 invert" />
        </div>
        
        <!-- svelte-ignore a11y_click_events_have_key_events -->
        <p class="ml-16 header-link" on:click={() => currentPage = 'song'}>Song</p>
        <!-- svelte-ignore a11y_click_events_have_key_events -->
        <p class="ml-16 header-link" on:click={() => currentPage = 'artist'}>Artist</p>
        <!-- svelte-ignore a11y_click_events_have_key_events -->
        <p class="ml-16 header-link" on:click={() => currentPage = 'saved'}>Saved</p>
      </div>
      {#if currentPage == 'song' || currentPage == 'artist'}
        <div class="flex justify-center text-white">
          <Card.Root class="w-1/2 mt-20">
            <Card.Header>
              <Card.Title class="flex justify-between">
                {#if currentPage == 'song'}
                  Song of the Day
                {:else}
                  Artist of the Day
                {/if}
                <Button variant="secondary" class="w-20" on:click={() => {
                  if(currentPage == 'song') {
                    savedItems = [...savedItems, "https://open.spotify.com/embed/track/3lsd1CbDC5ejAOJhPn5dB9?utm_source=generator&theme=0"];
                  } else {
                    savedItems = [...savedItems, "https://open.spotify.com/embed/artist/6bDWAcdtVR3WHz2xtiIPUi?utm_source=generator&theme=0"]
                  }
                  toast.success("Added to your saved items.")
                }}>Save</Button>
              </Card.Title>
            </Card.Header>
            <Card.Content>
              <div id="selection">
                {#if currentPage == 'song'}
                  <iframe title="Spotify embed of random selection" style="border-radius:12px" src={filterGenre != '' && filterLanguage != '' ? randomSongs[filterGenre][filterLanguage] : randomSongs['Pop']['Japanese'] } width="100%" height="152" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
                {:else}
                  <iframe title="Spotify embed of random artist" style="border-radius:12px" src={filterGenre != '' && filterLanguage != '' ? randomArtists[filterGenre][filterLanguage] : randomArtists['Pop']['Japanese']} width="100%" height="152" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
                {/if}
              </div>
            </Card.Content>
            <Card.Footer class="flex justify-between">
            </Card.Footer>
          </Card.Root>

        </div>

        <div class="flex justify-center text-white mt-8">
          <Tabs.Root value="popular" class="w-1/2 text-center">
            <Tabs.List>
              <Tabs.Trigger class="w-[120px]" value="popular">Popular 
                <Tooltip.Provider>
                  <Tooltip.Root>
                    <Tooltip.Trigger class="h-2 w-2">
                        <Info class="h-4 ml-1 mt-[-3px]" title="Most popular songs of the day" />
                    </Tooltip.Trigger>
                    <Tooltip.Content>
                      <p>Most popular songs of the day</p>
                    </Tooltip.Content>
                  </Tooltip.Root>
                </Tooltip.Provider>
              </Tabs.Trigger>
              <Tabs.Trigger class="w-[120px]" value="trending">Trending 
                <Tooltip.Provider>
                  <Tooltip.Root>
                    <Tooltip.Trigger class="h-2 w-2">
                        <Info class="h-4 ml-1 mt-[-3px]" title="Most trending songs of the day" />
                    </Tooltip.Trigger>
                    <Tooltip.Content>
                      <p>Most trending songs of the day</p>
                    </Tooltip.Content>
                  </Tooltip.Root>
                </Tooltip.Provider>
              </Tabs.Trigger>
              <Tabs.Trigger class="w-[120px]" value="indie">Indie
                <Tooltip.Provider>
                  <Tooltip.Root>
                    <Tooltip.Trigger class="h-2 w-2">
                        <Info class="h-4 ml-1 mt-[-3px]" title="Most popular indie songs of the day" />
                    </Tooltip.Trigger>
                    <Tooltip.Content>
                      <p>Indie songs are shown if the artist is below a certain threshold of <br> monthly listeners to not be considered "mainstream".</p>
                    </Tooltip.Content>
                  </Tooltip.Root>
                </Tooltip.Provider>
              </Tabs.Trigger>
            </Tabs.List>
            <Tabs.Content value="popular">
              
              <div class="flex justify-center">
                <Card.Root class="w-3/4">
                  <Card.Content>
                    <Table.Root>
                      <Table.Header>
                        <Table.Row>
                          <Table.Head class="w-[100px]">#</Table.Head>
                          <Table.Head>Song</Table.Head>
                          <Table.Head>Artist</Table.Head>
                        </Table.Row>
                      </Table.Header>
                      <Table.Body>
                        {#each popularSongs as item, i}
                          <Table.Row class="text-left">
                            <Table.Cell class="font-medium">{i+1}</Table.Cell>
                            <Table.Cell><div class="flex"><img src="{item.icon}" alt="song icon" class="size-8 mr-2 mt-[-5px]" />{item.name}</div></Table.Cell>
                            <Table.Cell>{item.artist}</Table.Cell>
                          </Table.Row>
                        {/each}
                          
                      </Table.Body>
                    </Table.Root>
                  </Card.Content>
                </Card.Root>
              </div>

            </Tabs.Content>
            <Tabs.Content value="trending">

              <div class="flex justify-center">
                <Card.Root class="w-3/4">
                  <Card.Content>
                    <Table.Root>
                      <Table.Header>
                        <Table.Row>
                          <Table.Head class="w-[100px]">#</Table.Head>
                          <Table.Head>Song</Table.Head>
                          <Table.Head>Artist</Table.Head>
                        </Table.Row>
                      </Table.Header>
                      <Table.Body>
                        {#each trendingSongs as item, i}
                          <Table.Row class="text-left">
                            <Table.Cell class="font-medium">{i+1}</Table.Cell>
                            <Table.Cell><div class="flex"><img src="{item.icon}" alt="song icon" class="size-8 mr-2 mt-[-5px]" />{item.name}</div></Table.Cell>
                            <Table.Cell>{item.artist}</Table.Cell>
                          </Table.Row>
                        {/each}
                      </Table.Body>
                    </Table.Root>
                  </Card.Content>
                </Card.Root>
              </div>

            </Tabs.Content>
            <Tabs.Content value="indie">

              <div class="flex justify-center">
                <Card.Root class="w-3/4">
                  <Card.Content>
                    <Table.Root>
                      <Table.Header>
                        <Table.Row>
                          <Table.Head class="w-[100px]">#</Table.Head>
                          <Table.Head>Song</Table.Head>
                          <Table.Head>Artist</Table.Head>
                        </Table.Row>
                      </Table.Header>
                      <Table.Body>
                        {#each indieSongs as item, i}
                          <Table.Row class="text-left">
                            <Table.Cell class="font-medium">{i+1}</Table.Cell>
                            <Table.Cell><div class="flex"><img src="{item.icon}" alt="song icon" class="size-8 mr-2 mt-[-5px]" />{item.name}</div></Table.Cell>
                            <Table.Cell>{item.artist}</Table.Cell>
                          </Table.Row>
                        {/each}
                      </Table.Body>
                    </Table.Root>
                  </Card.Content>
                </Card.Root>
              </div>
              
            </Tabs.Content>
          </Tabs.Root>
        </div>
      {:else}
        <div class="flex justify-center text-white">
          <Card.Root class="w-1/2 mt-20">
            <Card.Header>
              <Card.Title>
                Your Saved Songs and Artists
              </Card.Title>
            </Card.Header>
            <Card.Content>

              <ScrollArea class="h-[28rem] w-full">
                {#each savedItems as item, i}
                  <div id="selection" class="mb-4 flex gap-4" >
                    <Button variant="ghost" class="mt-2 h-2 text-white rounded-full px-1" on:click={() => {
                      savedItems.splice(i,1);
                      savedItems = [...savedItems];
                    }}>X</Button><iframe title="Spotify embed of random selection" style="border-radius:12px" src={item} width="90%" height="152" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
                  </div>
                {/each}
              </ScrollArea>
              
            </Card.Content>
            <Card.Footer class="flex justify-between">
            </Card.Footer>
          </Card.Root>

        </div>
      {/if}
      
      
    </div>
  {/if}
</main>
