<script lang="ts">
import {
  defineComponent,
  computed,
  ref,
  onMounted,
  onBeforeUnmount,
} from "vue";

export default defineComponent({
  name: "OrganismsProfile",
  setup() {
    const showModal = ref(false);

    const items = computed(() => {
      return [
        {
          text: "Javascript",
          description:
            "JavaScript é uma linguagem de programação para desenvolvimento web, adicionando interatividade e permitindo a criação de aplicativos complexos. É popular no front-end e back-end, suportando programação orientada a objetos, funcional e baseada em eventos.",
        },
        {
          text: "Typescript",
          description:
            "TypeScript é uma extensão rigorosa de JavaScript que incorpora tipagem estática opcional. Ele oferece uma camada adicional de segurança e previsibilidade ao código.",
        },
        {
          text: "PHP",
          description:
            "PHP é uma linguagem server-side para criar sites e aplicativos web dinâmicos. Ela é usada para processamento de formulários, geração de conteúdo dinâmico e interação com bancos de dados, sendo fácil de aprender e bem integrada com HTML.",
        },
        {
          text: "Css",
          description:
            "CSS (Cascading Style Sheets) é uma linguagem usada para estilizar e formatar documentos HTML. Ela controla a aparência de elementos em uma página web, como cores, fontes, espaçamentos e layout. CSS permite criar designs responsivos e atraentes para websites.",
        },
        {
          text: "Sass",
          description:
            "Sass é uma linguagem de extensão para CSS que adiciona funcionalidades como variáveis, aninhamento e mixins. Facilita a escrita de CSS de forma mais organizada e reutilizável, ajudando na criação de estilos complexos e na manutenção de grandes projetos de design.",
        },
        {
          text: "Json",
          description:
            "JSON é um formato leve para troca de dados, fácil de ler e escrever para humanos e simples de processar para máquinas. Ele usa uma estrutura de chave-valor e é comum em APIs e comunicação entre servidores e clientes.",
        },
        {
          text: "Vue",
          description:
            "Vue.js é um framework para criar interfaces de usuário interativas e dinâmicas. Ele oferece uma abordagem reativa para atualizar a interface com base nas mudanças de dados, e é conhecido por sua simplicidade, flexibilidade e fácil integração.",
        },
        {
          text: "Nuxt",
          description:
            "Nuxt.js é um framework para Vue.js que facilita o desenvolvimento de aplicativos web, incluindo sites estáticos e renderização do lado do servidor. Ele oferece configuração padrão, roteamento automático e suporte a módulos para criar aplicações escaláveis e otimizadas.",
        },
        {
          text: "MySQL",
          description:
            "MySQL é um sistema de banco de dados relacional de código aberto, amplamente usado para armazenar e gerenciar dados em aplicativos web e empresariais. Ele utiliza SQL para manipulação de dados e é conhecido por sua robustez e escalabilidade.",
        },
      ];
    });

    const copyInfo = () => {
      navigator.clipboard.writeText("Conteúdo copiado!").then(() => {
        showModal.value = true;
        setTimeout(() => (showModal.value = false), 2000);
      });
    };

    const currentYear = new Date().getFullYear();

    let observer: IntersectionObserver;

    onMounted(() => {
      observer = new IntersectionObserver((entries) => {
        entries.forEach((entry) => {
          entry.target.classList.toggle("visible", entry.isIntersecting);
        });
      });

      const modalElement = document.querySelector(".profile__modal");
      const footerElement = document.querySelector(".footer");

      if (modalElement) observer.observe(modalElement);
      if (footerElement) observer.observe(footerElement);
    });

    onBeforeUnmount(() => {
      if (observer) observer.disconnect();
    });

    return {
      items,
      copyInfo,
      showModal,
      currentYear,
    };
  },
});
</script>
<template>
  <div class="profile">
    <aside class="profile__modal">
      <div class="profile__modal__what">
        <AtomsParagraphtext
          text="Quem é Pedro Henrique?"
          size="small"
          types="default"
        />
        <h1 class="title">Quem é Pedro Henrique?</h1>
        <p class="text">
          Tenho 17 anos e sou desenvolvedor front-end na Braip, com 1,4 meses de
          experiência. Tenho domínio de JavaScript, TypeScript, Vue.js, Nuxt.js,
          Sass, CSS, HTML, Git, npm e ferramentas de banco de dados como
          Workbench e DBeaver-CE. Busco expandir para full-stack e criar
          soluções completas, sempre comprometido com a melhoria contínua e
          novos desafios no desenvolvimento web.
        </p>
      </div>
      <div class="profile__modal__card">
        <div
          v-for="(item, index) in items"
          :key="index"
          class="profile__modal__card__cards"
          @click="copyInfo"
        >
          <div class="profile__modal__card__cards--section">
            <AtomsParagraphTitle
              :text="item.text"
              size="small"
              types="default"
            />
            <AtomsParagraphTitle
              :text="item.description"
              size="extra-small"
              types="animation"
              class="text"
            />
          </div>
        </div>
      </div>
    </aside>
    <div v-if="showModal" class="copyInfo">
      <AtomsParagraphTitle
        text="Copiado!"
        size="extra-small"
        types="animation"
      />
    </div>
    <footer class="footer">
      <h5 class="footer__title">
        © {{ currentYear }} Pedro Henrique. Todos os direitos reservados.
      </h5>
    </footer>
  </div>
</template>
<style scoped lang="scss">
@import "styles.module.scss";
</style>
