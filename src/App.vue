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
      "mission_slug": "001",
      "current_md": "",
      "events": "",
      "missions": [


        {
          "slug": "001",
          "name": "4x4 Industry Solutions",
          "status": "start"
        },


        {
          "slug": "102",
          "name": "Revitalizing the Publishing Industry for Ghostwriters",
          "status": "start"
        },

     ],
      "pilots": [
        {
          "callsign": "Adalynn",
          "alias": "Adalynn Chantelle",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Perfoming Arts ",
          "mech": "Playwright"
        },

        {
          "callsign": "Alice",
          "alias": "Alice Adair",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Sales",
          "mech": "Account Executive"
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
          "callsign": "Andrej",
          "alias": "Andrej Bauer",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Automation ",
          "mech": "Project Manager"
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
          "callsign": "Batsukh",
          "alias": "Batsukh Lkhagvasuren",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Motivational Speaking ",
          "mech": "Guest Speaker"
        },


        {
          "callsign": "Berthold",
          "alias": "Berthold Mueller",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Small Business ",
          "mech": "Clerk"
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
          "callsign": "Carlos",
          "alias": "Carlos Rodriguez",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Recruitment ",
          "mech": "Headhunter"
        },


        {
          "callsign": "Carrie",
          "alias": "Carrie Castellano",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Community Services ",
          "mech": "Neighborhood Volunteer"
        },


        {
          "callsign": "Chandler",
          "alias": "Chandler von Hausen",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Self-Governance ",
          "mech": "Committee Chair"
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
          "callsign": "Craig",
          "alias": "Craig Conner",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Software Development ",
          "mech": "App Developer"
        },


        {
          "callsign": "Cynthia",
          "alias": "Cynthia Williams",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Consulting ",
          "mech": "Consultant"
        },


        {
          "callsign": "Destiny",
          "alias": "Destiny Smith",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Life Coaching ",
          "mech": "Life Coach"
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
          "callsign": "Gerald",
          "alias": "Gerald LeBlanc",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Legal ",
          "mech": "Lawyer"
        },


        {
          "callsign": "Giovanni",
          "alias": "Giovanni Rossi",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Coaching ",
          "mech": "Spiritual Coach"
        },


        {
          "callsign": "Helene",
          "alias": "Helene von Strudel",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Art And Special Events ",
          "mech": "Exhibitionist"
        },


        {
          "callsign": "Ivana",
          "alias": "Ivana Petrovic",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Metaverse & Vr ",
          "mech": "Developer"
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
          "callsign": "Janine",
          "alias": "Janine Jenkins",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Writing And Publishing ",
          "mech": "Ghostwriter"
        },


        {
          "callsign": "Jaxon",
          "alias": "Jaxon Petrescu",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Digital Marketing Services ",
          "mech": "Web Jedi"
        },


        {
          "callsign": "Lucie",
          "alias": "Lucie Dubois",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Advertising ",
          "mech": "Media Buyer"
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
          "callsign": "Marco",
          "alias": "Marco Fenech",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Financial Services ",
          "mech": "Investment Banker"
        },


        {
          "callsign": "Marcus",
          "alias": "Marcus Blackwood",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Money Lending ",
          "mech": "Bankroller"
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
          "callsign": "Martina",
          "alias": "Martina Garcia",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Support Group ",
          "mech": "Moderator"
        },


        {
          "callsign": "Michael",
          "alias": "Michael Mohanan",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Fiduciary & Security Services ",
          "mech": "Trustee"
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
          "callsign": "Orazali",
          "alias": "Orazali Jumabayev",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Philosophy And Higher Education ",
          "mech": "Philosopher"
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
          "callsign": "Pedro",
          "alias": "Pedro Sanchez",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Startup Services ",
          "mech": "Cofounder"
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
          "callsign": "Susanna",
          "alias": "Samantha Forester",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Finance ",
          "mech": "CFO"
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
          "callsign": "Tamar",
          "alias": "Tamar Kobalia",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Freelance ",
          "mech": "Digital Nomad"
        },


        {
          "callsign": "Tina",
          "alias": "Tina Kowalski",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Film ",
          "mech": "Screenwriter"
        },



        {
          "callsign": "Viktor",
          "alias": "Viktor Kuznetsov",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Consulting ",
          "mech": "Consultant"
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
