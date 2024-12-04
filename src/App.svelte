<!-- App.svelte -->

<script>
// @ts-nocheck

  import "./app.css";
  import { Info } from 'lucide-svelte';
  import { Button } from "$lib/components/ui/button/index.js";
  import * as Accordion from "$lib/components/ui/accordion/index.js";
  import * as Card from "$lib/components/ui/card/index.js";
  import * as Select from "$lib/components/ui/select/index.js";
  import { Input } from "$lib/components/ui/input/index.js";
  import { Label } from "$lib/components/ui/label/index.js";
  import * as Tabs from "$lib/components/ui/tabs/index.js";
  import * as Table from "$lib/components/ui/table/index.js";



  let currentPage = 'song';

  let popularSongs = [
    {
      icon: 'https://i.scdn.co/image/ab67616d0000b273283a117f2bc39bc4122692c0',
      name: 'Shoka',
      artist: 'Ado',
    },
    {
      icon: 'https://i.scdn.co/image/ab67616d0000b273283a117f2bc39bc4122692c0',
      name: 'Shoka',
      artist: 'Ado',
    },
    {
      icon: 'https://i.scdn.co/image/ab67616d0000b273283a117f2bc39bc4122692c0',
      name: 'Shoka',
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

</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Tangerine:wght@400;700&display=swap');
  .horizon {
  font-family: "Tangerine", cursive;
  font-weight: 700;
  font-style: normal;
}

  #main {
    background:linear-gradient(120deg, #1db954, #191414);
  }

  #random {
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

  {#if currentPage == 'home'}
  <div id="main" class="h-full">
    <div class="text-center">
      <div class="flex text-center justify-center">
        <p class="pt-56 text-white text-7xl font-bold ml-32 horizon">Horizon</p>
        <img src="https://freesvg.org/img/corbeau_Eighth_note.png" alt="Eighth Note" class="size-36 mt-32" />
      </div>
      <p class="text-white text-xl pb-10">Discover new horizons of music</p>
      <div class="flex items-center justify-center gap-4">
        <Button variant="hero" on:click={() => currentPage = 'song'}>Song</Button>
        <Button variant="hero" on:click={() => currentPage = 'song'}>Artist</Button>
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
            <Accordion.Trigger>Is there a limit?</Accordion.Trigger>
            <Accordion.Content>
              None! You can roll as many songs or artists as you like.
            </Accordion.Content>
          </Accordion.Item>
        </Accordion.Root>
      </div>
      
      
    </div>
  </div>
    
  {:else if currentPage == 'song' || currentPage == 'artist'}
    <div id="random" class="h-max w-full">
      <!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
      <div id="header" class="flex text-xl p-2 text-white">
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
        <p class="ml-16 header-link" on:click={() => currentPage = 'song'}>Saved</p>
      </div>

      <div class="flex justify-center text-white">
        <Card.Root class="w-1/2 mt-10">
          <Card.Header>
            <Card.Title>
              {#if currentPage == 'song'}
                Song of the Day
              {:else}
                Artist of the Day
              {/if}
            </Card.Title>
          </Card.Header>
          <Card.Content>
            <div id="selection">
              {#if currentPage == 'song'}
                <iframe title="Spotify embed of random selection" style="border-radius:12px" src="https://open.spotify.com/embed/track/3lsd1CbDC5ejAOJhPn5dB9?utm_source=generator&theme=0" width="100%" height="152" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
              {:else}
                <iframe title="Spotify embed of random artist" style="border-radius:12px" src="https://open.spotify.com/embed/artist/6bDWAcdtVR3WHz2xtiIPUi?utm_source=generator&theme=0" width="100%" height="152" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
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
            <Tabs.Trigger class="w-[120px]" value="popular">Popular <Info class="ml-2 h-4" /></Tabs.Trigger>
            <Tabs.Trigger class="w-[120px]" value="trending">Trending <Info class="ml-2 h-4" /></Tabs.Trigger>
            <Tabs.Trigger class="w-[120px]" value="indie">Indie <Info class="ml-2 h-4" /></Tabs.Trigger>
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
      
    </div>
  {/if}
</main>
