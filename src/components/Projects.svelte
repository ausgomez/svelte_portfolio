<script>
import { scale, slide } from 'svelte/transition';
let projects = 
[
    { id: 'Web-3D-Maps', title: 'Web 3D Maps', desc: 'A web app to help people find their buildings around certain area. Like for example a university or city', latest: true, category: 'web', tags: ['vue', 'node', 'vuetify', 'mapbox'], source: '', live: ''},

    { id: 'Habanero-App', title: 'Habanero App', desc: 'This is an open-source Flutter app that I developed to suggest food recipes based on the ingredients that the user already have', latest: true, category: 'mobile', tags: ['flutter', 'Android', 'ios', 'firebase'], source: 'https://github.com/Anstroy/recipe_app_flutter', live: ''},

    { id: 'Svelte-Portfolio', title: 'Svelte Portfolio', desc: 'A portolio template made with Svelte, this website exact website is the project', latest: true, category: 'web', tags: ['svelte', 'bootstrap'], source: 'https://github.com/Anstroy/svelte_portfolio', live: 'https://anstroy.github.io'},

    { id: 'Ketogram', title: 'Ketogram', desc: 'Simply send a photo of your favorite food to this phone number (956) 403-6287 and you will receive information about that food being keto friendly or not.', latest: false, category: 'mobile', tags: ['python', 'flask', 'twilio'], source: 'https://github.com/Anstroy/ketogram', live: ''},

    { id: 'Clienthub', title: 'Clienthub', desc: 'This is one of my very first medium-sized Ruby on Rails projects. It was developed for a company that needed a solution to keep a track of their clients personal information. It also includes file upload/download. The source code is NOT on github I have it on my personal private Bitbucket.', latest: false, category: 'web', tags: ['rails', 'bootstrap', 'postgresql'], source: '', live: 'https://clienthub.herokuapp.com/'},

    { id: 'Veterinary-App', title: 'Veterinary App', desc: `This is a platform built for a Veterinary company in Mexico, it's goal was to have a track of the customers and their pets.`, latest: false, category: 'web', tags: ['rails', 'bootstrap', 'postgresql'], source: '', live: 'https://vetapp19.herokuapp.com/en/'},

    { id: 'Chat-Room', title: 'Chat Room', desc: 'This project was created using Vue.js + Firebase as backend, it allows any person to enter to a global chatroom using a desired nickname', latest: false, category: 'web', tags: ['vue', 'node', 'firebase'], source: 'https://github.com/Anstroy/ninja-chat-vue-cli', live: 'https://ninja-chat-d3150.web.app/'},

    { id: 'Grading-Mini-App', title: 'Grading Mini App', desc: 'Basic school grading app, made using only VUE.js and nothing else', latest: false, category: 'web', tags: ['vue', 'node', 'firebase'], source: 'https://github.com/Anstroy/grading_app', live: 'https://grading-aus.firebaseapp.com/'}
]

let singleProject = projects[0];

let filteredProjects = projects;
let current = 0;

function setFilter(cat) {
      cat == 'all' ? filteredProjects = projects 
    : filteredProjects = projects.filter(p => p.category == cat)

    filteredProjects.sort(function(a, b) {
    return a - b;
    });
}

</script>

<div class="project-filter">
    <h2>Projects</h2>
    <div class="btn-group" role="group" aria-label="Filter projects">
        <button class:active="{current === 0}" on:click={() => {setFilter('all'); current = 0}} type="button" class="btn btn-lg btn-info">All Projects</button>
        <button class:active="{current === 1}" on:click={() => {setFilter('web'); current = 1}} type="button" class="btn btn-lg btn-info">Web Dev</button>
        <button class:active="{current === 2}" on:click={() => {setFilter('mobile'); current = 2}} type="button" class="btn btn-lg btn-info">Mobile Apps</button>
    </div>
    <br>
    <div class="btn-group resume" role="group" aria-label="Third group">
        <a href="/files/resume.pdf" class="btn btn-sm btn-outline-primary"><i class="fas fa-download"></i> Get Resume</a>
    </div>
</div>
<div class="row projects">
    {#each filteredProjects as project, i}
    <div class="col-xs-6 col-sm-6 col-md-4 col-lg-3 card-div text-center" transition:scale>
        {#if project.latest}<span class="badge badge-pill latest" in:slide>Latest</span>{/if}
        <a href="#" on:click={()=>{singleProject=project}} data-toggle="modal" data-target="#singleProjectModal" class="item-portfolio-static gallery masonry_item portfolio-33-33 cat--1">
            <div class="portfolio-static">
                <div class="thumbnail-inner">
                    <div class="thumbnail">
                        <img class="img-fluid" src="/projects/{project.id}.png" 
                        alt="{project.id}" width="auto" height="200">
                    </div>
                </div>
                <div class="content">
                <p></p>
                    <div class="inner">
                        <h4>{project.title}</h4>
                        <p>
                        {#each project.tags as tag, i}
                            <img src="/icons/{tag}.png" alt="" class="image" width="30px">&nbsp;&nbsp;
                        {/each}
                        </p>
                    </div>
                </div>
            </div>
        </a>
    </div>
    {/each}
</div>

<!-- Modal -->
<div class="modal fade" id="singleProjectModal" tabindex="-1" role="dialog" aria-labelledby="singleProjectModalLabel" aria-hidden="true">
  <div class="modal-dialog modal-xl" role="document">
    <div class="modal-content">
      <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">
            <i class="fas fa-times"></i>
          </span>
        </button>
        <div class="modal-body text-center">
          <div class="container">
            <div class="row justify-content-center">
              <div class="col-lg-8">
                <!-- Portfolio Modal - Title -->
                <h2 class="portfolio-modal-title text-secondary text-uppercase mb-0">{singleProject.title}</h2>
                <!-- Icon Divider -->
                <div class="divider-custom">
                  <div class="divider-custom-line"></div>
                  <div class="divider-custom-line"></div>
                </div>
                <!-- Portfolio Modal - Image -->
                <img class="img-fluid rounded mb-5" style="max-width: 20em;" src="/projects/{singleProject.id}.png" alt="">
                <!-- Technologies -->
                <h6>Technologies used:</h6>
                <h5>
                {#each singleProject.tags as tag, i}
                  <span class="badge badge-pill badge-default"> <img src="/icons/{tag}.png" alt="" class="image" width="30px"></span>&nbsp;
                {/each}
                </h5>
                <p></p>
                <!-- Portfolio Modal - Text -->
                <p class="mb-5">{singleProject.desc}</p>
                {#if singleProject.live != ''}
                <a class="btn btn-primary text-white" href="{singleProject.live}" target="_blank">
                  <i class="fas fa-eye"></i>
                    Live Demo
                </a>
                {/if}

                {#if singleProject.source != ''}
                <a class="btn btn-info text-white" href="{singleProject.source}" target="_blank">
                  <i class="fab fa-github"></i>
                    Source Code
                </a>
                {/if}
              </div>
            </div>
          </div>
        </div>
    </div>
  </div>
</div>



<style>
    .latest{
        font-size: 20px;
        position: absolute;
        left: 0;
        background-color: #F5820B;
        color: white;
    }
    .project-filter{
        margin: 10px 0;
        text-align: center;
    }
    .projects{
        text-align: center;
		padding: 10px 50px;
	}

	.card-div{
        padding-top: 10px;
		margin: 20px 0;
        background-color: #F8F9FC;
	}

    .card-div:hover{
		background-color: #eaeaea;
        margin-top: 15px;
	}

    a.item-portfolio-static
    {
        text-decoration: none;
        color: black;
    }
</style>