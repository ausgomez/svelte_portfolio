<script>
let projects = 
[
    { name: 'PRoject 1', text: 'something jaja' },
    { name: 'PRoject 1', text: 'something jaja' },
    { name: 'PRoject 1', text: 'something jaja' },
    { name: 'PRoject 1', text: 'something jaja' },
]


</script>


<div class="row projects">
    {#each projects as project, i}
    <div class="col-sm-12 col-md-6 col-lg-4 card-div text-center">
        <a href="" class="item-portfolio-static gallery masonry_item portfolio-33-33 cat--1">
            <div class="portfolio-static">
                <div class="thumbnail-inner">
                    <div class="thumbnail">
                        <img class="img-fluid" src="https://picsum.photos/500/300?image={i + 10}" 
                        alt="Portfolio Images" width="auto" height="200">
                    </div>
                </div>
                <div class="content">
                    <div class="inner">
                        <p>Web Design</p>
                        <h4>T-shirt design is the part of design</h4>
                    </div>
                </div>
            </div>
        </a>
    </div>
    {/each}
</div>



<style>
    .projects{
		padding: 30px 50px;
	}

	.card-div{
		margin-top: 20px;
	}

    a.item-portfolio-static
    {
        text-decoration: none;
        color: black;
    }
</style>