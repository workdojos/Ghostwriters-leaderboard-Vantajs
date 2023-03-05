<template>
  <Header :header="this.header" />
  <div class="content-container">
    <section class="section-container" id="missions" style="width:435px; height:714px;">
      <div class="section-header clipped-medium-backward">
        <img src="/icons/mission-icon.svg" />
        <h1>Background</h1>
      </div>
      <div class="section-content-container">
        <h3>Current Assignment</h3>
        <Markdown :source="current_md" class="markdown" />
        <h3>Mission List</h3>
        <div class="mission-list-container">
          <Mission
            v-for="item in this.missions"
            :key="item.slug"
            :mission="item"
            :selected="this.mission_slug"
            @click="selectMission(item)"
          />
        </div>
      </div>
    </section>
    <section class="section-container" id="pilots" style="width:894px; height:714px;">
      <div style="height:52px; overflow:hidden;">
        <div class="section-header clipped-medium-backward-pilot">
          <img src="/icons/pilot-icon.svg" />
          <h1>Roster</h1>
        </div>
        <div class="rhombus-back">&nbsp;</div>
      </div>
      <div class="section-content-container">
        <div class="pilot-list-container">
          <Pilot v-for="item in this.pilots" :key="item.slug" :pilot="item" />
        </div>
      </div>
    </section>
  </div>
  <svg
    style="visibility: hidden; position: absolute;"
    width="0"
    height="0"
    xmlns="http://www.w3.org/2000/svg"
    version="1.1"
  >
    <defs>
      <filter id="round">
        <feGaussianBlur in="SourceGraphic" stdDeviation="5" result="blur" />
        <feColorMatrix
          in="blur"
          mode="matrix"
          values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 19 -5"
          result="goo"
        />
        <feComposite in="SourceGraphic" in2="goo" operator="atop" />
      </filter>
    </defs>
  </svg>
  <audio autoplay>
    <source src="/startup.ogg" type="audio/ogg" />
  </audio>
  <Footer/>
</template>

<script>
import Header from './components/layout/Header.vue';
import Footer from './components/layout/Footer.vue';
import Mission from './components/Mission.vue';
import Pilot from './components/Pilot.vue';
import Markdown from 'vue3-markdown-it';

export default {
  components: {
    Header,
    Footer,
    Mission,
    Pilot,
    Markdown
  },

  data() {
    return {
      "mission_slug": "102",
      "current_md": "",
      "events": "",
      "missions": [

        {
          "slug": "1",
          "name": "Choose your profession and domain name",
          "status": "start"
        },

        {
          "slug": "2",
          "name": "Become familiar with your dashboard",
          "status": "start"
        },

        {
          "slug": "3",
          "name": "Gain SSH access to your server",
          "status": "start"
        },
        

        {
          "slug": "4",
          "name": "Become familiar with your Nextcloud Hub",
          "status": "start"
        },
        

        {
          "slug": "5",
          "name": "Customize your Wordpress site",
          "status": "start"
        },
        

        {
          "slug": "6",
          "name": "Customize your Ghost blog",
          "status": "start"
        },

        {
          "slug": "7",
          "name": "Customize your Wiki",
          "status": "start"
        },


        {
          "slug": "8",
          "name": "Customize your chat server",
          "status": "start"
        },


        {
          "slug": "9",
          "name": "Review and save essential Linux commands",
          "status": "start"
        },


        {
          "slug": "10",
          "name": "Secure your server with Fail2ban",
          "status": "start"
        },


        {
          "slug": "11",
          "name": "Create a logo",
          "status": "start"
        },


        {
          "slug": "12",
          "name": "Create social media handles",
          "status": "start"
        },


        {
          "slug": "13",
          "name": "Customize social media channels",
          "status": "start"
        },


        {
          "slug": "14",
          "name": "Write and publish your first blog",
          "status": "start"
        },


        {
          "slug": "15",
          "name": "Write and save your first Wiki entry",
          "status": "start"
        },


        {
          "slug": "16",
          "name": "Assemble digital assets",
          "status": "start"
        },


        {
          "slug": "17",
          "name": "Research 5 challenges facing your industry",
          "status": "start"
        },


        {
          "slug": "18",
          "name": "Research 5 recent innovations affecting your profession",
          "status": "start"
        },


        {
          "slug": "19",
          "name": "Compile a list of 5 competitors in your space",
          "status": "start"
        },


        {
          "slug": "20",
          "name": "Compile a list of 5 influential people operating in your industry",
          "status": "start"
        },


        {
          "slug": "21",
          "name": "Start a free trial with Buffer and schedule 10 posts to your social media channels",
          "status": "start"
        },


        {
          "slug": "22",
          "name": "Compile a list of 15 Reddit threads related to your mission",
          "status": "start"
        },


        {
          "slug": "23",
          "name": "Network with 5 contacts or organizations",
          "status": "start"
        },


        {
          "slug": "24",
          "name": "Schedule 5 additional blog posts",
          "status": "start"
        },

        {
          "slug": "25",
          "name": "Create a business plan",
          "status": "start"
        },

        {
          "slug": "26",
          "name": "Create a pitch deck",
          "status": "start"
        },

        {
          "slug": "27",
          "name": "Add an additional teammate",
          "status": "start"
        },



        {
          "slug": "28",
          "name": "Pitch 3 investors",
          "status": "start"
        },



        {
          "slug": "29",
          "name": "Register a company",
          "status": "start"
        },



        {
          "slug": "30",
          "name": "Register a trademark",
          "status": "start"
        },



        {
          "slug": "31",
          "name": "Create a newsletter",
          "status": "start"
        },



        {
          "slug": "32",
          "name": "Identify paid media opportunities",
          "status": "start"
        },



        {
          "slug": "33",
          "name": "Write a whitepaper",
          "status": "start"
        },



        {
          "slug": "34",
          "name": "Host a webinar",
          "status": "start"
        },
        {
          "slug": "35",
          "name": "Host a local event",
          "status": "start"
        },
        {
          "slug": "100",
          "name": "Revitalizing the Publishing Industry for Ghostwriters",
          "status": "start"
        },

     ],
      "pilots": [


        {
          "callsign": "Janine",
          "alias": "Janine Jenkins",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Writing And Publishing ",
          "mech": "Ghostwriter"
        },


        {
          "callsign": "Amadou",
          "alias": "Amadou Diop",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Public Relations ",
          "mech": "PR Rep"
        },


        {
          "callsign": "Ani",
          "alias": "Ani Gevorkian",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Translation & Interpretation ",
          "mech": "Interpreter"
        },


        {
          "callsign": "Bhimsen",
          "alias": "Bhimsen Shrestha",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Writing & Publishing ",
          "mech": "Novelist"
        },


        {
          "callsign": "Chuka",
          "alias": "Chuka Udeze",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Marketing Services ",
          "mech": "Lead Generator"
        },


        {
          "callsign": "Dirk",
          "alias": "Dirk Mueller",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Consulting ",
          "mech": "Strategist"
        },


        {
          "callsign": "Farida",
          "alias": "Farida Juraeva",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Web Design ",
          "mech": "Web Designer"
        },


        {
          "callsign": "Francesca",
          "alias": "Francesca Rodriguez",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Special Events ",
          "mech": "Event Planner"
        },


        {
          "callsign": "Jacob",
          "alias": "Jacob Trainer",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Server Administration ",
          "mech": "System Administrator"
        },




        {
          "callsign": "Marcia",
          "alias": "Marcia Merriweather",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Administration & Book-Keeping ",
          "mech": "Administrator"
        },


        {
          "callsign": "Marta",
          "alias": "Marta Kowalski",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Journalism, News, And Media ",
          "mech": "Photo Journalist"
        },


        {
          "callsign": "Michelle",
          "alias": "Michelle Ziegler",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Journalism ",
          "mech": "Correspondent"
        },


        {
          "callsign": "Milos",
          "alias": "Milos Djordjevic",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Broader Business ",
          "mech": "Project Manager"
        },


        {
          "callsign": "Paula",
          "alias": "Paula Randall",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Marketing ",
          "mech": "Digital Marketer"
        },


        {
          "callsign": "Petra",
          "alias": "Petra Kostas",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Graphic Design And Graphic Arts ",
          "mech": "Graphic Designer"
        },


        {
          "callsign": "Selma",
          "alias": "Selma Hadzic",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Scientific Research & Development ",
          "mech": "Researcher"
        },



        {
          "callsign": "Sofia",
          "alias": "Sofia Silva",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Content Creation ",
          "mech": "Content Creator"
        },


        {
          "callsign": "Misty",
          "alias": "Misty Gomez",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Sales & Marketing ",
          "mech": "Social Media Manager"
        },


        {
          "callsign": "Tina",
          "alias": "Tina Kowalski",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Film ",
          "mech": "Screenwriter"
        },





      ],
      "header": {
        "planet": "DOJO's WORLD (coming soon)",
        "year": "2023",
        "system": "Foundry VTT",
        "gate": "PUBLIC",
        "ring": "workdojos.com",
        "headerTitle": "DOJOS",
        "headerSubtitle": "COMPENDIUM",
        "subheaderTitle": "BUILT WITH VANTA.JS",
        "subheaderSubtitle": "MISSION BRIEF",
      },
      "options":{
        "eventsMarkdownPerMission": true
      }
    }
  },

  created() {
    this.loadMissionMarkdown()
    this.loadEventsMarkdown()
  },

  computed: {

  },

  methods: {
    selectMission(mission) {
      this.mission_slug = mission.slug;
      this.loadMissionMarkdown()
      if(this.options.eventsMarkdownPerMission){
        this.loadEventsMarkdown();
      }
    },
    loadMissionMarkdown() {
      let self = this;
      let md = `/missions/${self.mission_slug}.md`
      var client = new XMLHttpRequest();
      client.open('GET', md);
      client.onreadystatechange = function () {
        self.current_md = client.responseText;
      }
      client.send();
    },
    loadEventsMarkdown() {
      let self = this;
      let md = "";

      if(self.options.eventsMarkdownPerMission){
        md = `/events/${self.mission_slug}.md`
      }
      else {
        md = "/events.md"
      }

      var client = new XMLHttpRequest();
      client.open('GET', md);
      client.onreadystatechange = function () {
        self.events = client.responseText;
      }
      client.send();
    }
  }

}
</script>


<style lang="scss">
#app {
  width: 1440px;
  height: 1440px;
  overflow: hidden;
}
</style>
