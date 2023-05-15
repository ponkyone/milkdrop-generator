<template>
 <div class="body">
    <h2>Entrez votre formule ( optionnel )</h2>
    <textarea name="" id="" cols="30" rows="10" style="width:80%margin:auto 10%"></textarea>
    <button @click="generateMilk">generate Milkdrop</button>
    <div class="box"></div>
    <p style="display:none" class="code">{{code}}</p>
</div>
</template>
<script>



export default {
  name: 'MilkGenerator',
  props: {
    msg: String,
    code:String
  },
  methods : {
  

    generateMilk() {
            for (let p = 0 ;p < 1 ;p++) {
                let nbWave = getRandomInt(20)
                let nbShape = getRandomInt(5)
                generateHeader()
                for (let nb = 0 ;nb < nbWave ;nb++) {
                    generateWave()
                }
                for (let nb = 0 ;nb < nbShape ;nb++) {
                    generateShape()
                }
                generateFooter()
                console.log(data)
                document.querySelector('.box').style.display="block"
                var csv = data
                var blob = new Blob([decodeURIComponent('%ef%bb%bf') /*prepend bom*/, csv], { type: 'text/csvcharset=utf-8' })
                var url = URL.createObjectURL(blob)
                var a = document.createElement('a')
                a.href = url
                a.download = 'milk.milk'
                document.body.appendChild(a)
                a.click()
            }
        }

        
  }
  }


        let header = ''
        let wave = ''
        let shape = ''
        let i = 0
        let z = 0
        let data = ''

         function getRandomInt(max) {
            return Math.floor(Math.random() * max)
        }
        function getRandom (){
            return Math.round(Math.random() * 1000000) / 1000000
        }
       
        function generateHeader() {
            header = '[preset00]' + '\n' +
                'fDecay=' + getRandom() + '\n' +
                'nWaveMode=' + getRandomInt(7) + '\n' +
                'bMaximizeWaveColor=' + getRandomInt(2) + '\n' +
                'fWaveAlpha=1' + '\n' +
                'fWaveScale=1.5' + '\n' +
                'fZoomExponent=1.000000' + '\n' +
                'zoom=1.000000' + '\n' +
                'warp=0.000000' + '\n' +
                'sx=1.000000' + '\n' +
                'sy=1.000000' + '\n' +
                'wave_r=' + getRandomInt(2) + '\n' +
                'wave_g=' + getRandomInt(2) + '\n' +
                'wave_b=' + getRandomInt(2) + '\n' +
                'wave_a=' + getRandomInt(2) + '\n' +
                'wave_x=0.500000' + '\n' +
                'wave_y=0.5000000' + '\n'
            document.querySelector('.box').append('header generated</br>')
            document.querySelector('.code').append(header)
            data = header
        }
        function generateWave() {
            wave = 'wavecode_' + i + '_enabled=' + getRandomInt(2) + '\n' +
                'wavecode_' + i + '_bDrawThick=' + getRandomInt(2) + '\n' +
                'wavecode_' + i + '_bAdditive=' + getRandomInt(2) + '\n' +
                'wavecode_' + i + '_scaling=1.000000' + '\n' +
                'wavecode_' + i + '_smoothing=' + getRandom() + '\n' +
                'wavecode_0_samples='+ getRandomInt(1024) + '\n' +
                'wavecode_0_sep=0' + '\n' +
                'wavecode_0_bSpectrum=0' + '\n' +
                'wavecode_0_bUseDots='+ getRandomInt(2) + '\n' +
                'wavecode_0_bDrawThick='+ getRandomInt(2) + '\n' +
                'wavecode_0_bAdditive='+ getRandomInt(2)  + '\n' +
                'wavecode_0_scaling=1.0' + '\n' +
                'wavecode_0_smoothing=0.5' + '\n' +
                'wavecode_' + i + '_r=' + getRandomInt(2) + '\n' +
                'wavecode_' + i + '_g=' + getRandomInt(2) + '\n' +
                'wavecode_' + i + '_b=' + getRandomInt(2) + '\n' +
                'wavecode_' + i + '_a=' + getRandomInt(2) + '\n'
            document.querySelector('.box').append('wave' + i + ' generated</br>')
            i++
            document.querySelector('.code').append(wave)
            data = data + wave
        }
        function generateShape() {
            shape = 'shapecode_' + z + '_enabled=' + getRandomInt(2) + '\n' +
                'shapecode_' + z + '_sides=' + getRandomInt(10) + '\n' +
                'shapecode_' + z + '_additive=' + getRandomInt(2) + '\n' +
                'shapecode_' + z + '_thickOutline=' + getRandomInt(2) + '\n' +
                'shapecode_' + z + '_textured=' + getRandomInt(2) + '\n' +
                'shapecode_' + z + '_num_inst=' + getRandomInt(1024) + '\n' +
                'shapecode_' + z + '_x=' + getRandom() + '\n' +
                'shapecode_' + z + '_y=' + getRandom() + '\n' +
                'shapecode_' + z + '_rad=' + getRandom() + '\n' +
                'shapecode_' + z + '_ang=' + getRandom() + '\n' +
                'shapecode_' + z + '_tex_ang=' + getRandom() + '\n' +
                'shapecode_' + z + '_tex_zoom=' + getRandom() + '\n' +
                'shapecode_' + z + '_r=' + getRandom() + '\n' +
                'shapecode_' + z + '_g=' + getRandom() + '\n' +
                'shapecode_' + z + '_b=' + getRandom() + '\n' +
                'shapecode_' + z + '_a=' + getRandom() + '\n' +
                'shapecode_' + z + '_r2=' + getRandom() + '\n' +
                'shapecode_' + z + '_g2=' + getRandom() + '\n' +
                'shapecode_' + z + '_b2=' + getRandom() + '\n' +
                'shapecode_' + z + '_a2=' + getRandom() + '\n' +
                'shapecode_' + z + '_border_r=' + getRandom() + '\n' +
                'shapecode_' + z + '_border_g=' + getRandom() + '\n' +
                'shapecode_' + z + '_border_b=' + getRandom() + '\n' +
                'shapecode_' + z + '_border_a=' + getRandom() + '\n' +
                document.querySelector('.box').append('shape' + z + ' generated</br>')
            z++
            document.querySelector('.code').append(shape)
            data = data + shape
        }
        function generateFooter() {
            let footer = document.querySelector('textarea').value
            if (footer == '') {
                footer = 'per_frame_1=wave_r = wave_r + 0.5*sin(1.2*frame) + 0.3*sin(1.9*frame)' + '\n' +
                    'per_frame_2=wave_g = wave_g + 0.7*sin(1.1*frame) + 0.4*cos(1.6*frame)' + '\n' +
                    'per_frame_3=wave_b = wave_b + 0.2*sin(1.3*frame) + 0.4*sin(2*frame)' + '\n' +
                    'per_pixel_1=rot=rot + (0.5 + 0.1*sin(bass)-rad)*pow(bass,3)/50' + '\n' +
                    'per_pixel_2=zoom= zoom + (0.5 + 0.3*tan(3*bass_att)-rad)*(cos(pow(rad,2.4))+(0.2*mid_att))' + '\n' +
                    'per_pixel_3=warp = warp + if (above(bass,1.34), 0.5*(0.5+ 0.1*sin(bass)-rad)*(cos(pow(rad,2.4))+(5*bass_att)), 0)' + '\n'
            }
            document.querySelector('.box').append('footer generated</br>')
            document.querySelector('.code').append(footer)
            data = data + footer
        }


    </script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>



        .box {
            display: none;
            margin: 0 10%;
            background-color: black;
            color: green;
            padding: 20px;
            font-family: 'Courier New', Courier, monospace;
            height: 200px;
            overflow-x: hidden;
            overflow-y: auto;
            text-align:left;
        }
        button {
            margin: auto;
            display: block;
            width: auto;
            background: red;
            padding: 2em;
            text-align: center;
            color: #fff;
            text-transform: uppercase;
            cursor: pointer;
            height: 100px;
            border: none;
            margin-bottom: 10px;
            margin-top: 10px;
        }
        h1 ,h2,p{

            text-align: center;
 
        }
        div { text-align:center;}
        .footer{height:60px;background-color:#000;text-align:center;line-height:60px;color:#fff;margin-top:50px;}
        .footer a {color:red;}

    
</style>
