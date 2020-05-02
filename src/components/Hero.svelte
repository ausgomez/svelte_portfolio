<script>
let visible = false;

    setTimeout(() => visible = true, 500);

	function typewriter(node, { speed = 50 }) {
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
        <img width="394" height="394" class="hero-image rounded-circle" src="http://rainbowit.net/html/trydo/assets/images/about/designer-avatar.png" alt="">
    </div>
    <div class="col-sm-12 col-lg-7 mt_md--40 mt_sm--40">
        <div class="inner">
        
        <span class="heading">Welcome to my World</span>
            {#if visible}
            <h1 class="title"><span in:typewriter>Hi, I’m Aus Gomez</span><br>
                <span class="second" in:typewriter> Software Developer.</span> 
            </h1>
            <h2  in:typewriter>based in USA.</h2>
            {/if}
        </div>
    </div>
</div>

<style>
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
    }
</style>