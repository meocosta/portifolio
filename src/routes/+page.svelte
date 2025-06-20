<script lang="ts">
    import "./page.scss";
    import exemplo from "./exemplinhos.json";

    const colors=["FFBE0B", "FB5607", "FF006E", "8338EC", "3A86FF"]

</script>

<section id="content">
    <h3 id="tituloPaginaInicial">passeio por pedaços de projetos</h3>
    <div>
        {#each exemplo as exemplo}
            <a href="/exemplinhos/{exemplo.href}">
                <div
                    id={exemplo.href}
                    class="exemplos"
                    style="background-image: {exemplo.foto
                        ? `url('src/routes/exemplinhos/${exemplo.href}/${exemplo.href}.png')`
                        : 'none'}"
                >
                    <div id="preto">
                        <h4 style="color:#{colors[Math.floor(Math.random() * colors.length)]}">{exemplo.nome}</h4>
                        <p>{exemplo.descrição}</p>
                    </div>
                </div>
            </a>
        {/each}
    </div>
</section>
