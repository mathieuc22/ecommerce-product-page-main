<template>
    <header class="row">
        <img class="logo" alt="Sneakers logo" src="../assets/logo.svg" />
        <div class="hamburger">
            <div class="hamburger__line"></div>
            <div class="hamburger__line"></div>
            <div class="hamburger__line"></div>
        </div>
        <nav class="navigation">
            <ul class="navlist">
                <li class="navlist__item hover-underline">Collections</li>
                <li class="navlist__item hover-underline">Men</li>
                <li class="navlist__item hover-underline">Women</li>
                <li class="navlist__item hover-underline">About</li>
                <li class="navlist__item hover-underline">Contact</li>
            </ul>
        </nav>
        <nav class="authentication">
            <ul class="navlist">
                <li class="navlist__item"><img src="src/assets/images/icon-cart.svg" alt="Icon cart"></li>
                <li class="navlist__item"><img class="avatar" src="src/assets/images/image-avatar.png"
                        alt="User avatar"></li>
            </ul>
        </nav>
    </header>
</template>

<style lang="scss">
header {
    height: 112px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    color: $color-neutral-Dark-grayish-blue;
    border-bottom: 1px solid $color-neutral-Grayish-blue;

    @media screen and (max-width: 400px) {
        padding: 40px 25px;
    }

    p {
        margin-left: 1rem;
    }
}

.navigation {
    height: 100%;
    margin-left: 2.3rem;

    @media screen and (max-width: 400px) {
        display: none;
    }
}

.authentication {
    margin-left: auto;

    @media screen and (max-width: 400px) {
        display: none;
    }
}

.navlist {
    height: 100%;
    font-size: 15px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 2.1rem;

    &__item {
        position: relative;
        height: 100%;
        display: inline-flex;
        align-items: center;

        &:hover {
            cursor: pointer;
            color: $color-neutral-Black;
        }
    }
}

.avatar {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    border: 2.5px solid transparent;
    margin-left: 10px;

    &:hover {
        border: 2.5px solid $color-primary-Orange;
    }
}

.hamburger {
    display: none;


    @media screen and (max-width: 400px) {
        display: flex;
        flex-direction: column;
        gap: 6px;
    }

    &__line {
        width: 24px;
        height: 3px;

    }
}

.hover-underline {
    cursor: pointer;

    &:after {
        content: "";
        position: absolute;
        width: 100%;
        transform: scaleY(0) translateX(-50%);
        height: 4px;
        bottom: 0;
        left: 50%;
        background-color: $color-primary-Orange;
        transition: all 0.2s ease-in-out;
    }

    &:hover:after {
        transform: scaleY(1) translateX(-50%);
    }
}
</style>