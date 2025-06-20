<script lang="ts">
    import "./page.scss";
    import Pause from "../static/pausar.svg";
    import Continuar from "../static/continuar.svg";
    import { onMount } from "svelte";

    let intervalId: number;
    let embaralhando = true;

    let SelectedImagem: Array<any> = [];

    let Imagem = [
        {
            txt: "amigos alegram a vida",
            href: "amgs",
        },
        {
            txt: "um sorvete da liberdade",
            href: "coisas",
        },
        {
            txt: "um bolso incrível de um menino do insta",
            href: "coisinhas",
        },
        {
            txt: "comidinha da paulista",
            href: "comidinha",
        },
        {
            txt: "ah, oi! Sou eu!",
            href: "eu",
        },
        {
            txt: "Yo nadando",
            href: "eu2",
        },
        {
            txt: "fotinha",
            href: "eu3",
        },
        {
            txt: "um hotel em Campos",
            href: "paisagem",
        },
        {
            txt: "bora rezar cmg?",
            href: "terço",
        },
    ];

    let controller = [0, 1, 2, 3, 4, 5, 6, 7, 8];

    function embaralhar(array: Array<number>) {
        for (let i = array.length - 1; i > 0; i--) {
            const j = Math.floor(Math.random() * (i + 1));
            [array[i], array[j]] = [array[j], array[i]]; // troca
        }
        return array;
    }

    function imagensEmbaralhando() {
        embaralhando = true;
        intervalId = setInterval(() => {
            controller = embaralhar(controller);
            for (let i = 0; i < Imagem.length; i++) {
                SelectedImagem[i] = Imagem[controller[i]];
            }
        }, 3000);
    }

    function pararImagens() {
        clearInterval(intervalId);
        embaralhando = false;
    }

    onMount(() => {
        imagensEmbaralhando();
    });
</script>

<section id="GaleriaVivaSection">
    <h4 id="Titulogaleria">galeria viva</h4>

    <section id="galeria">
        {#each SelectedImagem as imagem}
            <div
                class="imagem"
                style={`background-image: url('/src/routes/exemplinhos/static/${imagem.href}.jpg')`}
            >
                <div id="pretoGaleria"></div>
                <div id="txt">
                    <p class="txtImagem">{imagem.txt}</p>
                    <button
                        on:click={() =>
                            embaralhando
                                ? pararImagens()
                                : imagensEmbaralhando()}
                    >
                        {#if embaralhando}
                            <!-- Ícone de pause -->
                            <svg
                                width="20"
                                height="20"
                                viewBox="0 0 24 24"
                                fill="none"
                                stroke="currentColor"
                                stroke-width="2"
                                stroke-linecap="round"
                                stroke-linejoin="round"
                                xmlns="http://www.w3.org/2000/svg"
                            >
                                <rect x="6" y="4" width="4" height="16"></rect>
                                <rect x="14" y="4" width="4" height="16"></rect>
                            </svg>
                        {:else}
                            <!-- Ícone de play -->
                            <svg
                                width="20"
                                height="20"
                                viewBox="0 0 24 24"
                                fill="none"
                                stroke="currentColor"
                                stroke-width="2"
                                stroke-linecap="round"
                                stroke-linejoin="round"
                                xmlns="http://www.w3.org/2000/svg"
                            >
                                <polygon points="5 3 19 12 5 21 5 3"></polygon>
                            </svg>
                        {/if}
                    </button>
                </div>
            </div>
        {/each}
    </section>
</section>
