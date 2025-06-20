<script>
    import "./page.scss";

    let controller = false;

    let conteudos = [
        {
            nome: "minha religião",
            text: "Uma coisa que fala muito sobre mim é minha religião. Sou católica praticante e estou na caminhada de tentar a santidade. Espero que eu esteja dando meu melhor e possa estar agradando a Deus",
        },
        {
            nome: "Meus Santos de Devoção",
            text: "Entre meus Santos de devoção, estão: São Carlo Acutis, Santa Rita de Cássia, São Frei Galvão, Santa Joana Dark e São Bento. Meu título Mariano Favorito é Nossa Senhora de Guadalupe!",
        },
    ];

    let select = conteudos[0];

    setInterval(() => {
        controller = !controller;
    }, 10000);

    $: controller ? (select = conteudos[0]) : (select = conteudos[1]);
</script>

<h2 id="titulo">Carrocel de duas Informações</h2>
<div id="bolinhas">
    <div class="ball" style="background-color: {controller ? '#FF006E' : '#BFCCD1FF'}"></div>
    <div class="ball" style="background-color: {controller ? '#BFCCD1FF' : '#FF006E'}"></div>
</div>
<section id="carrocel" style="flex-direction: {controller ? 'row' : 'row-reverse'};">
    <div id="titleDiv">
        <h3>{select.nome}</h3>
    </div>
    <div>
        <p>{select.text}</p>
    </div>
</section>
