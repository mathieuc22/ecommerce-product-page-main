<template>

    <div class="cart">
        <h2 class="cart__title">Cart</h2>
        <div class="cart__content">
            <p>Your cart is empty.</p>
        </div>

    </div>


</template>

<style lang="scss" scoped>
.cart {
    height: 250px;
    width: 360px;
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%) translateY(110%);
    border-radius: 10px;
    background-color: $color-neutral-White;
    box-shadow: 0px 20px 30px 0px rgb(0 0 0 / 20%);
    cursor: initial;

    &__title {
        font-size: 1em;
        color: $color-neutral-Black;
        width: 100%;
        height: 26%;
        padding: 25px;
        border-bottom: 1px solid $color-neutral-Grayish-blue;

    }

    &__content {
        display: flex;
        align-items: center;
        justify-content: center;
        height: 74%;
        font-weight: 700;
    }
}
</style>