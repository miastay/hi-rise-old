<script>
    import { Card, CardText, CardTitle, Tabs, Tab, Window, WindowItem, Select, TextField, Col, Dialog, Switch } from "svelte-materialify";
    import ColorPick from "./ColorPick.svelte";
    let value = 0;

    let plotWidth = 1200;
    let plotHeight = 600;

    let significanceCorrection = "Bonferroni"
    let significanceValue = 0.05;
    let showSignificance = false;

    let colors = {
        points: "#33dd00",
        significant: "#ff00ff"
    }

    const palettes = {
        "hi-rise": {
            points: "#44ee22",
            significant: "#22e2ef"
        },
        "black and white": {
            points: "#000000",
            significant: "#101010"
        }
    }
    let selectedPalette = "hi-rise"
    $: updatePalette(selectedPalette)

    function updatePalette(pal) {
        console.log(pal)
        colors = {...palettes[pal]}
        console.log(showSignificance)
    }

</script>

<div class="options">
    <Card outlined style="height: 100%">
        <Tabs class="primary-text" bind:value fixedTabs>
            <div slot="tabs">
              <Tab class="tab">Rendering</Tab>
              <Tab class="tab">Tab 2</Tab>
              <Tab class="tab">Item 3</Tab>
            </div>
          </Tabs>
          <Window {value}>
            <WindowItem>
                <div class="windowinner">
                    <div>
                        <div class="item">
                            <span>Resolution: </span>
                            <div class="sm">
                                <TextField dense outlined bind:value={plotWidth}>w</TextField>
                            </div>x
                            <div class="sm">
                                <TextField dense outlined bind:value={plotHeight}>h</TextField>
                            </div>
                        </div>
                        <div class="item">
                            <span>Show significance line? </span>
                            <Switch bind:checked={showSignificance}></Switch>
                        </div>
                        {#if showSignificance}
                            <div class="item">
                                <span>Hypothesis correction: </span>
                                <div class="min">
                                    <Select dense outlined items={["Bonferroni", "FDR", "Not adjusted"]} bind:value={significanceCorrection}></Select>
                                </div>
                                <div class="sm">
                                    <TextField dense outlined bind:value={significanceValue}></TextField>
                                </div>
                            </div>
                        {/if}
                    </div>
                    <div class="section">
                        <div class="item spread">
                            <span class="title">Colors</span>
                            <Select dense outlined items={Object.keys(palettes)} bind:value={selectedPalette}>Palette</Select>
                        </div>
                        <button on:click={() => console.log(selectedPalette)}>click 4 colors</button>
                        <div class="item">
                            <ColorPick bind:color={colors.points} name={"All Points"}/>
                        </div>
                        <div class="item">
                            <ColorPick bind:color={colors.significant} name={"Significant Points"}/>
                        </div>
                    </div>
                </div>
            </WindowItem>
            <WindowItem>
              <h4>Item 2</h4>
              <p>
                Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec accumsan, diam et
                elementum gravida, arcu mi fermentum nibh, vel dapibus ligula orci non est. Morbi
                commodo sagittis finibus. Maecenas in volutpat massa. Nullam vulputate metus velit,
                quis interdum elit imperdiet ut. Suspendisse et sagittis erat, euismod vulputate
                enim. Etiam feugiat sit amet justo vitae commodo.
              </p>
            </WindowItem>
            <WindowItem>
              <h4>Item 3</h4>
              <p>
                Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec accumsan, diam et
                elementum gravida, arcu mi fermentum nibh, vel dapibus ligula orci non est. Morbi
                commodo sagittis finibus. Maecenas in volutpat massa. Nullam vulputate metus velit,
                quis interdum elit imperdiet ut. Suspendisse et sagittis erat, euismod vulputate
                enim. Etiam feugiat sit amet justo vitae commodo.
              </p>
            </WindowItem>
          </Window>
    </Card>
</div>

<style lang="scss">
    .windowinner {
        padding: 1rem;
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 1rem;
        .item {
            display: flex;
            flex-direction: row;
            gap: 0.5rem;
            align-items: center;
            .sm {
                max-width: 60px;
            }
            .min {
                max-width: 140px;
            }
            &.spread {
                justify-content: space-between;
            }
        }
        .section {
            .title {
                font-size: 1.3rem;
                font-weight: 600;
            }
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }
    }
</style>