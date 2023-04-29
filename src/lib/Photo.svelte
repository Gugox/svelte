<script>
    export let img;
    export let desc;
</script>

<div class="container">
    <div class="container_photo">
        <div>
            <img src={img} alt="" />
        </div>
        <p>Id photo {desc}</p>
    </div>
</div>

<style>

    .container_photo > div {
            display: inline-block;
            margin-right: 20px;
            width: 500px;
            height: 300px;
            background-color: black;
        }
    
        .container_photo {
            display: inline-block;
            margin-right: 20px;
        }
    
        img {
            width: 100%;
            height: 100%;
        }
    
    </style>
    