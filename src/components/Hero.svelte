<script>
import { scale, slide } from 'svelte/transition';
let first = false;
let second = false;
let third = false;
let fourth = false;

    setTimeout(() => first = true, 500);
    setTimeout(() => second = true, 1200);
    setTimeout(() => third = true, 1700);
    setTimeout(() => fourth = true, 1900);

	function typewriter(node, { speed = 30 }) {
		const valid = (
			node.childNodes.length === 1 &&
			node.childNodes[0].nodeType === Node.TEXT_NODE
		);

		if (!valid) {
			throw new Error(`This transition only works on elements with a single text node child`);
		}

		const text = node.textContent;
		const duration = text.length * speed;

		return {
			duration,
			tick: t => {
				const i = ~~(text.length * t);
				node.textContent = text.slice(0, i);
			}
		};
	}
</script>

<div class="row align-items-center">
    <div class="col-sm-12 col-lg-5  text-center">
        <img width="394" height="394" class="hero-image rounded-circle" src="/aus.jpg" alt="">
    </div>
    <div class="col-sm-12 col-lg-7 mt_md--40 mt_sm--40">
        <div class="inner">
        
        <span class="heading">Welcome to my Portfolio</span>
            
            <h1 class="title">
                {#if first}
                <span in:typewriter>Hi, I’m Aus Gomez</span>
                {/if}
                <br>
                {#if second}
                <span class="second" in:typewriter> Software Developer.</span> 
                {/if}
            </h1>
            {#if third}
            <h2  in:typewriter>based in USA.</h2>
            {/if}
        </div>
        <br>
        {#if fourth}
        <div class="links" in:scale>
            <a href="https://www.linkedin.com/in/austreberto-gomez-a85822113/" title="Aus Linkedin" target="_blank">
                <span class="fa-stack fa-2x">
                    <i class="fas fa-circle fa-stack-2x" style="color:#1FA4B6"></i>
                    <i class="fab fa-linkedin fa-stack-1x fa-inverse"></i>
                </span>
            </a>
            
            <a href="https://github.com/Anstroy" title="Anstroy Github" target="_blank">
                    <span class="fa-stack fa-2x">
                        <i class="fas fa-circle fa-stack-2x" style="color:black"></i>
                        <i class="fab fa-github fa-stack-1x fa-inverse"></i>
                    </span>
                </a>
            
            <a href="https://www.instagram.com/auscode.me/" title="Aus Instagram" target="_blank">
                <span class="fa-stack fa-2x">
                    <i class="fas fa-circle fa-stack-2x" style="color:#F44D56"></i>
                    <i class="fab fa-instagram fa-stack-1x fa-inverse"></i>
                </span>
            </a>

            <a href="https://www.freecodecamp.org/anstroy" title="Aus FreeCodeCamp" target="_blank">
                <span class="fa-stack fa-2x">
                    <i class="fas fa-circle fa-stack-2x" style="color:#1B1B32"></i>
                    <i class="fab fa-free-code-camp fa-stack-1x fa-inverse"></i>
                </span>
            </a>
            
        </div>
        {/if}
    </div>
</div>

<style>
    div.links{
        text-align: left;
    }

    div.links a{
        text-decoration: none;
    }

    div.links a:hover{
        font-size: large;
    }
   
    div.inner h1.title, h2 {
        font-family: 'Montserrat', sans-serif;
    }

    .row{
        padding: 150px 0;
        background: #F8F9FC;
    }

    .hero-image{
        border-radius: 100%;
        padding: 0;
        border: 14px solid #fff;
        -webkit-box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1), 0 20px 40px rgba(255, 255, 255, 0.15);
        box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1), 0 20px 40px rgba(255, 255, 255, 0.15);
    }

    .row span.heading{
        color: #1f1f25;
        font-size: 15px;
        text-transform: uppercase;
        letter-spacing: 4px;
        display: block;
        margin-bottom: 20px;
    }

    h1.title{
        width: 100%;
        font-size: 58px;
        line-height: 75px;
    }

    span.second {
        color: #1FA4B6;
    }

    @media only screen and (max-width: 1199px) and (min-width: 992px)
    {
        div.inner{
            text-align: left;
        }

        h1.title {
            font-size: 58px;
            line-height: 75px;
        }
    }

    @media only screen and (max-width: 1199px) and (min-width: 992px)
    {
        h1.title {
            font-size: 70px;
        }
    }

    @media only screen and (max-width: 1199px) and (min-width: 992px)
    {
        h1.title {
            font-size: 90px;
            line-height: 103px;
        }
    }

    @media only screen and (max-width: 991px){
        div.inner{
            margin-top: 100px;
            text-align: center;
        }

        div.links{
            text-align: center;
        }
    }
</style>