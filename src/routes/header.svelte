<script lang="ts">
    import "./header.scss";
    let nameControll = false;
    let name = [
        {
            text: "Maria's",
            id: "mari",
        },
        {
            text: "Monalisa's",
            id: "mona",
        },
    ];

    let nomeSelected = name[0];

    const changeName = (value: boolean) => {
        nameControll = value;
    };

    $: {
        if (nameControll) {
            nomeSelected = name[1];
        } else {
            nomeSelected = name[0];
        }
    }
</script>

<section>
    <header>
        <h2>bem vindo ao meu portifólio, se sinta a vontade</h2>
        <hr>
        <div>
            <h1
                class="nome {nomeSelected.id}"
                onmouseenter={() => {
                    changeName(true);
                }}
                onmouseleave={() => {
                    changeName(false);
                }}
            >
                {nomeSelected.text}
            </h1>
            <h1>portifólio</h1>
        </div>
        <hr>
        <h2>English? No, we're <span>Brasilians</span></h2>
    </header>
</section>
