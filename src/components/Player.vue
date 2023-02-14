<template>
    <div id="playerDiv"></div>
</template>

<script>
export default {
    'name': 'NanoPlayer',
    data() {
        const streamNames = ['HX26g-NRbx9', 'HX26g-uVn3M', 'HX26g-VbAxm'];
        return {
            'config': {
                'source': {
                    'defaults': {
                        'service': 'bintu'
                    },
                    'entries': [
                        {
                            'index'  : 0,
                            'label'  : 'stream 1',
                            'h5live' : {
                                'rtmp': {
                                    'streamname': streamNames[0]
                                }
                            }
                        },
                        {
                            'index'  : 1,
                            'label'  : 'stream 2',
                            'h5live' : {
                                'rtmp': {
                                    'streamname': streamNames[1]
                                }
                            }
                        },
                        {
                            'index'  : 2,
                            'label'  : 'stream 3',
                            'h5live' : {
                                'rtmp': {
                                    'streamname': streamNames[2]
                                }
                            }
                        }
                    ],
                    'options': {
                        'adaption': {
                            'rule': 'deviationOfMean2'
                        }
                    },
                    'startIndex': 2
                },
                'playback': {
                    'autoplay' : true,
                    'automute' : true,
                    'muted'    : false
                },
                'style': {
                    'displayMutedAutoplay' : true,
                    'fullScreenControl'    : true
                }
            }
        };
    },
    'mounted': function () {
        var nanoPlayer = new window.NanoPlayer('playerDiv');
        nanoPlayer.setup(this.config).then(
            function (config) {
                console.log('setup success');
                console.log('config: ' + JSON.stringify(config, undefined, 4));
            },
            function (error) {
                alert(error.message);
            }
        );
    }
};
</script>
