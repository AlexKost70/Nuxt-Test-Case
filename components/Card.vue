<template>
  <div class="card" :id="id" @click="showModal(id)">
    <img :src="picture" :alt="name">
    <div class="card-footer">
      <p>name: <span>{{ name }}</span></p>
      <p>email: <span>{{ email }}</span></p>
    </div>
    <div class="wrapper" v-show="modalVisible[id]">
      <div class="modal">
        <a class="close" @click.stop="hideModal(id)"><img :src="closeImage" /></a>
        <img class="photo" :src="picture">
        <div class="modal-footer">
          <p>name: <span>{{ name }}</span></p>
          <p>age: <span>{{ age }}</span></p>
          <p>email: <span>{{ email }}</span></p>
          <p>phone: <span>{{ phone }}</span></p>
          <p>about: <span>{{ about }}</span></p>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
  .hidden {
    display: none;
  }

  .card {
    width: 380px;
    height: 405px;
    border-radius: 20px;
    border: 1px solid #F1F1F1;
    box-shadow: 0px 4px 10px 3px rgba(148, 148, 148, 0.25);
  }

  .card-footer {
    display: flex;
    flex-direction: column;
    gap: 15px;
    padding: 43px 17.1px;
    padding-bottom: 0;
  }

  .card > img {
    border-top-right-radius: 20px;
    border-top-left-radius: 20px;
    width: 380px;
    height: 244px;
    object-fit: cover;
    object-position: center 5%;
  }

  .card p {
    color: var(--gray);
    font-size: 21px;
    font-style: normal;
    font-weight: 700;
    display: flex;
    align-items: center;
    gap: 5px;
  }

  .card p span {
    display: inline-block;
    color: var(--black);
    font-weight: 400;
    max-width: 270px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  .wrapper {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background: rgba(79, 79, 79, 0.62);
  }

  .modal {
    max-width: 980px;
    max-height: 880px;
    border-radius: 20px;
    box-shadow: 0px 4px 10px 3px rgba(148, 148, 148, 0.25);
    position: fixed;
    margin: auto;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    background-color: var(--white);
  }

  .modal .close {
    width: 60px;
    height: 60px;
    position: absolute;
    right: -30px;
    top: -30px;
    cursor: pointer;
  }

  .modal .photo {
    border-top-left-radius: 20px;
    border-top-right-radius: 20px;
    width: 100%;
    height: 480px;
    object-fit: cover;
    object-position: center -30px;
  }

  .modal-footer {
    padding: 33px 17px 33px 34px;
    display: flex;
    flex-direction: column;
    gap: 15px;
  }

  .modal-footer p {
    align-items: start;
  }

  .modal-footer p span {
    max-width: 858px;
    white-space: wrap;
  }

  @media (max-height: 945px), (max-width: 1050px) {
    .modal {
      overflow-x: scroll;
    }

    .modal .close {
      top: 30px;
      right: 3vw;
      position: fixed;
    }
  }

  @media (max-width: 375px) {
    .card,
    .card > img {
      max-width: 100%;
    }
  }
</style>

<script>
  import closeImage from "../assets/close.svg";
  export default {
    name: 'Card',
    data() {
      return {
        modalVisible: {},
        closeImage: closeImage
      };
    },
    props: {
      id: String,
      picture: String,
      age: Number,
      name: String,
      email: String,
      phone: String,
      about: String
    },
    methods: {
      showModal(id) {
        this.$set(this.modalVisible, id, true);
        document.querySelector("body").style.overflow = "hidden";
      },
      hideModal(id) {
        this.$set(this.modalVisible, id, false);
        document.querySelector("body").style.overflow = "auto";
      }
    }
  }
</script>
