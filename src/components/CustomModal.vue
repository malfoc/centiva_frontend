<template>
    <div>
        <div class="button-container">
            <button class="btn btn-primary" @click="showModal = true; buttonType = 'info'">Info</button>
            <button class="btn btn-success" @click="showModal = true; buttonType = 'success'">Success</button>
            <button class="btn btn-warning" @click="showModal = true; buttonType = 'warning'">Warning</button>
            <button class="btn btn-danger" @click="showModal = true; buttonType = 'alert'">Alert</button>
        </div>

        <div class="modal" tabindex="-1" role="dialog" v-if="showModal">
            <div class="modal-dialog" role="document">
                <div class="modal-content">
                    <div class="modal-header" v-bind:class="buttonType">
                        <button
                            type="button"
                            class="btn-close"
                            data-bs-dismiss="modal"
                            aria-label="Close"
                            @click="showModal = false"></button>
                    </div>
                    <div class="modal-body">
                        <div class="row">
                            <div class="col-2">
                                <span v-if="buttonType === 'info'" class="bi bi-info-circle-fill"></span>
                                <span v-if="buttonType === 'success'" class="bi bi-check-circle-fill"></span>
                                <span v-if="buttonType === 'warning'" class="bi bi-exclamation-triangle-fill"></span>
                                <span v-if="buttonType === 'alert'" class="bi bi-exclamation-circle-fill"></span>
                            </div>
                            <div class="col-10">
                                <div class="row">
                                    <div class="col">
                                        <p class="title">Ceci le titre d'une modale de succès</p>
                                    </div>
                                </div>
                                <div class="row">
                                    <div class="col">
                                        <p  class="content">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed hendrerit est
                                            sit amet sapien dignissim, nec dictum leo varius.</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="modal-footer d-flex justify-content-between align-items-center">
                        <div class="form-check">
                            <div v-if="buttonType === 'info'">
                                <input class="form-check-input" type="checkbox" value="" id="testCheckbox">
                                <label class="form-check-label" for="testCheckbox">
                                    Ne plus afficher
                                </label>
                            </div>
                        </div>
                        <div>
                            <button type="button" class="btn btn-secondary mr-2" data-bs-dismiss="modal" @click="showModal = false">Annuler</button>
                            <button type="button" class="btn" 
                                :class="{'btn-primary': buttonType === 'info', 'btn-success': buttonType === 'success', 'btn-warning': buttonType === 'warning', 'btn-danger': buttonType === 'alert'}"
                                @click="showModal = false">Confirmer</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>

<style lang="scss">
    $color-accent1-normal: #0d6efd;
    $color-accent6-normal: #198754;
    $color-accent8-normal: #FFCA2C;
    $color-accent9-normal: #BB2D3B; 

    .button-container button {
        margin-right: 16px;
    }

    .modal {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background-color: rgba(0, 0, 0, 0.5);
        display: flex;
        justify-content: center;
        align-items: center;

        .modal-dialog {
            max-width: 580px;
            width: 90vw;
        }

        .modal-content {
            background-color: white;
            padding: 0;

            .modal-header {
                padding: 16px;
                border-top: 5px solid;

                .close {
                    float: right;
                    font-size: 10px;
                    font-weight: 700;
                    line-height: 1;
                    color: #000000;
                    opacity: 0.5;

                    &:focus,
                    &:hover {
                        color: #000000;
                        opacity: 0.75;
                        text-decoration: none;
                    }
                }
            }

            .modal-header.info {
                border-top-color: $color-accent1-normal;
            }

            .modal-header.success {
                border-top-color: $color-accent6-normal;
            }

            .modal-header.warning {
                border-top-color: $color-accent8-normal;
            }

            .modal-header.alert {
                border-top-color: $color-accent9-normal;
            }

            .modal-body {
                padding: 36px;

                .row {
                    margin-bottom: 16px;

                    &:last-child {
                        margin-bottom: 0;
                    }

                    .col-2 {
                        text-align: center;

                        .bi-info-circle-fill {
                            color: $color-accent1-normal;
                        }
                        .bi-check-circle-fill {
                            color: $color-accent6-normal;
                        }
                        .bi-exclamation-triangle-fill {
                            color: $color-accent8-normal;
                        }
                        .bi-exclamation-circle-fill {
                            color: $color-accent9-normal;
                        }
                    }

                    .col-10 {
                        text-align: left;

                        .title {
                            font-weight: bold;
                            font-size: large;
                        }

                        .content {
                            color: #565656
                        }
                    }
                }
            }

            .modal-footer {
                padding: 12px 16px;

                .btn-secondary.mr-2 {
                    margin-right: 12px;
                }

                .row {
                    .col {
                        padding: 0 16px;
                    }

                    &:last-child {
                        margin-top: 12px;
                    }
                }
            }
        }
    }
</style>

<script>
    export default {
        data() {
            return {
                showModal: false,
                buttonType: null,
            };
        },
        methods: {}
    };
</script>