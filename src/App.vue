<template>
    <div id="app">

        <button type="button" class="btn btn-success btn-sm rounded-pill btn-custom" data-toggle="modal" data-target="#exampleModal">
            UNLOCK
        </button>

        <!-- Modal -->
        <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
            <div class="modal-dialog">
                <div class="modal-content border-0 p-3">
                    <div class="modal-header p-0 pb-4">
                        <h5 class="modal-title text-light" id="exampleModalLabel">Unlock Player</h5>
                        <button type="button" class="close text-light" data-dismiss="modal" aria-label="Close">
                            <span aria-hidden="true">&times;</span>
                        </button>
                    </div>
                    <div class="modal-body p-0">
                        <div class="unlock-player__wrapper position-relative w-100 h-100">
                            <img src="/img/unlock-player.jpg" width="648" height="596" class="desktop" alt="unlock-player">
                            <img src="/img/unlock-player_mobile.jpg" width="370" height="606" class="mobile" alt="unlock-player">
                        </div>
                        <div v-show="showMessage" class="unlock-warning-message__wrapper position-absolute w-100 h-100">
                            <div class="warning-message__header position-relative w-100">
                                <div class="message-icon">
                                    <div class="icon-wrapper">
                                        <img src="/img/player.png" width="80" height="82" class="player" alt="player">
                                        <img src="/img/lock.png" width="33" height="40" class="lock" alt="lock">
                                    </div>
                                </div>
                                <div class="message-title">
                                    <div class="skeleton-title rounded-sm bg-light mb-1"/>
                                    <div class="skeleton-subtitle rounded-sm bg-light mb-3"/>
                                    <div class="progress mb-1">
                                        <div class="progress-bar bg-light" role="progressbar" style="width: 100%" aria-valuenow="25" aria-valuemin="0" aria-valuemax="100"></div>
                                    </div>
                                    <span class="text-light">CONTRIBUTE TO REACH 100%</span>
                                </div>
                            </div>
                            <div class="warning-message__body position-relative w-100">
                                <h2 class="text-light mb-4">First, let’s see how it works</h2>
                                <ul>
                                    <li class="mb-4">
                                        <div class="list-title mb-2">
                                            <span class="icon mr-2">
                                                <i class="fa fa-check text-light"></i>
                                            </span>
                                            <h3 class="d-inline text-light mb-0">Buy at pre-market price</h3>
                                        </div>
                                        <div class="list-subtitle">Buy up to 10% of the initial 10k shares at “pre-market” price and also provide initial liquidity to the market.</div>
                                    </li>
                                    <li class="mb-4">
                                        <div class="list-title mb-2">
                                            <span class="icon mr-2">
                                                <i class="fa fa-check text-light"></i>
                                            </span>
                                            <h3 class="d-inline text-light mb-0">Help expand the market</h3>
                                        </div>
                                        <div class="list-subtitle">Once unlock is completed, the player will be available to trade in the market.</div>
                                    </li>
                                    <li>
                                        <div class="list-title mb-2">
                                            <span class="icon mr-2">
                                                <i class="fa fa-check text-light"></i>
                                            </span>
                                            <h3 class="d-inline text-light mb-0">Work as a team to unlock</h3>
                                        </div>
                                        <div class="list-subtitle">Share the unlock link with other users to pool your funds and unlock players faster.</div>
                                    </li>
                                </ul>
                            </div>
                            <div class="warning-message__footer position-relative w-100">
                                <div class="footer-wrapper position-relative w-100 h-100">
                                    <div class="help">
                                        Have questions? <a href="https://help.tradestars.app/en/" target="_blank" rel="noopener noreferrer">Learn more</a>
                                    </div>
                                    <div class="call-to-action">
                                        <button type="button" class="btn btn-success rounded-pill btn-custom" @click="showMessage = false">UNDERSTOOD</button>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>

<script>
import $ from 'jquery';

export default {
    name: 'app',

    data() {
        return {
            showMessage: true,
        };
    },

    mounted() {
        $('#exampleModal').on('show.bs.modal', () => { this.showMessage = true; });
    },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";

* {
    box-sizing: border-box;
}

#app {
    position: relative;
    width: 100%;
    height: 100vh;
    padding: 1rem;
    background-color: #fff;
    font-family: 'Roboto', sans-serif;
    color: #000;

    .btn {
        &.btn-custom {
            padding: 6px 15px;
            font-weight: 500;
        }
        &:focus {
            outline: none;
            box-shadow: none;
        }
    }

    .modal {
        > .modal-dialog {
            max-width: 640px;

            > .modal-content {
                background-color: #222;
                border-radius: 12px;

                > .modal-header {
                    border-bottom: none;

                    > .modal-title {
                        letter-spacing: .6px;
                    }

                    > .close {
                        opacity: 1;
                        > span {
                            font-size: 2rem;
                            font-weight: 200;
                        }
                    }
                }

                > .modal-body {
                    > .unlock-player__wrapper {
                        > img {
                            width: 100%;
                            height: 100%;

                            &.desktop {
                                display: block;
                            }
                            &.mobile {
                                display: none;
                            }
                        }
                    }
                    > .unlock-warning-message__wrapper {
                        padding: 2rem;
                        top: 0;
                        left: 0;
                        display: grid;
                        grid-template-columns: 1fr;
                        grid-template-rows: 82px 1fr 82px;
                        gap: 20px;
                        background-color: #333;
                        border-radius: 9px;

                        > .warning-message__header {
                            display: grid;
                            grid-template-columns: 80px 1fr;
                            grid-template-rows: auto;
                            align-content: center;
                            gap: 30px;

                            > .message-icon {
                                position: relative;
                                width: 100%;
                                height: 100%;
                                display: flex;
                                justify-content: center;
                                align-content: center;

                                > .icon-wrapper {
                                    position: relative;
                                    width: 80px;
                                    height: 82px;
                                    > img.player {
                                        //
                                    }
                                    > img.lock {
                                        position: absolute;
                                        top: 0;
                                        right: -15px;
                                    }
                                }
                            }
                            > .message-title {
                                > .skeleton-title {
                                    width: 115px;
                                    height: 12px;
                                    opacity: .17;
                                }
                                > .skeleton-subtitle {
                                    width: 85px;
                                    height: 8px;
                                    opacity: .08;
                                }
                                > .progress {
                                    height: 8px;
                                }
                                > span {
                                    font-size: 12px;
                                    font-weight: 500;
                                }
                            }
                        }

                        > .warning-message__body {
                            > h2 {
                                font-size: 22px;
                                font-weight: 400;
                            }
                            > ul {
                                padding-left: 0;
                                list-style: none;

                                > li {
                                    > div {
                                        &.list-title {
                                            display: inline-flex;
                                            > h3 {
                                                font-size: 16px;
                                                font-weight: 300;
                                            }
                                        }
                                    }
                                    > .list-subtitle {
                                        font-size: 14px;
                                        font-weight: 300;
                                        color: #c1c1c1;
                                    }
                                }
                            }
                        }

                        > .warning-message__footer {
                            display: flex;
                            align-items: flex-end;

                            > .footer-wrapper {
                                display: flex;
                                justify-content: space-between;
                                align-items: flex-end;
                                > .help {
                                    font-size: 15px;
                                    color: #c1c1c1;
                                }
                            }
                        }
                    }
                }
            }
        }

        @media screen and (max-width: 639px) {
            > .modal-dialog {
                margin: 0;
                width: 100%;
                max-width: 100%;

                > .modal-content {
                    height: 100vh;
                    border-radius: 0;

                    > .modal-body {

                        > .unlock-player__wrapper {
                            > img {
                                &.desktop {
                                    display: none;
                                }
                                &.mobile {
                                    display: block;
                                }
                            }
                        }

                        > .unlock-warning-message__wrapper {
                            padding: 1.5rem;
                            > .warning-message__footer {
                                > .footer-wrapper {
                                    flex-direction: column-reverse;
                                    align-items: center;

                                    > .call-to-action {
                                        width: 100%;
                                        > .btn {
                                            width: 100%;
                                        }
                                    }
                                }
                            }
                            > .warning-message__body {
                                overflow-y: auto;
                            }
                        }
                    }
                }
            }
        }
    }

}
</style>
