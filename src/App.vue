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
          <h1>Pilot Roster</h1>
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
      "mission_slug": "Template",
      "current_md": "",
      "events": "",
      "missions": [
        {
          "slug": "Template",
          "name": "Template",
          "status": "start"
        },
        {
          "slug": "Template",
          "name": "Template",
          "status": "start"
        },
        {
          "slug": "Template",
          "name": "Template",
          "status": "start"
        },
        {
          "slug": "Template",
          "name": "Template",
          "status": "start"
        },
        {
          "slug": "Template",
          "name": "Template",
          "status": "start"
        },
        {
          "slug": "Template",
          "name": "Template",
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
          "callsign": "Adia",
          "alias": "Adia Ndume",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Physical Therapy ",
          "mech": "Physical Therapist"
        },


        {
          "callsign": "Akiko",
          "alias": "Akiko Tanaka",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Complementary And Alternative Medicine ",
          "mech": "Healer"
        },


        {
          "callsign": "Alex",
          "alias": "Alex Theodorus",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Outdoor ",
          "mech": "Explorer"
        },


        {
          "callsign": "Alexander",
          "alias": "Alexander Arrondale",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Startup Financing ",
          "mech": "Financier"
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
          "callsign": "Ana",
          "alias": "Ana Rodriguez",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Healthcare ",
          "mech": "Healthcare Professional"
        },


        {
          "callsign": "Adia",
          "alias": "Adia Ndume",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Physical Therapy ",
          "mech": "Physical Therapist"
        },

        {
          "callsign": "Anders",
          "alias": "Anders Lindqvist",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Digital Preservation ",
          "mech": "Digital Preservation Specialist"
        },


        {
          "callsign": "Andreas",
          "alias": "Andreas Papadopoulos",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Infectious Diseases ",
          "mech": "Pathologist"
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
          "callsign": "Andris",
          "alias": "Andris Liepa",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Healthcare ",
          "mech": "Practitioner"
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
          "callsign": "Anna",
          "alias": "Anna Gruber",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Animal Sciences ",
          "mech": "Zookeeper"
        },


        {
          "callsign": "Audrey",
          "alias": "Audrey Abigail",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Cafe ",
          "mech": "Cafe Owner"
        },


        {
          "callsign": "Avi",
          "alias": "Avi Cohen",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Luxury Goods ",
          "mech": "Jeweler"
        },


        {
          "callsign": "Bahar",
          "alias": "Bahar Bahar",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Non-Profit Organizations  ",
          "mech": "Non-Profit"
        },


        {
          "callsign": "Barry",
          "alias": "Barry Baker",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Legislative ",
          "mech": "Legislator"
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
          "callsign": "Becca",
          "alias": "Becca Bristow",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Backpacking ",
          "mech": "Traveler"
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
          "callsign": "Blythe",
          "alias": "Blythe Beckminster",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Outdoor Adventure ",
          "mech": "Adventurer"
        },


        {
          "callsign": "Carla",
          "alias": "Carla Murphy",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Higher Education ",
          "mech": "College Professor"
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
          "callsign": "Cheng Li",
          "alias": "Cheng Li Li",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Manufacturing ",
          "mech": "Manufacturer"
        },


        {
          "callsign": "Chikondi",
          "alias": "Chikondi Mwale",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Machining ",
          "mech": "Machinist"
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
          "callsign": "Consuela",
          "alias": "Consuela Hernandez",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Retail ",
          "mech": "Retailer"
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
          "callsign": "Derek",
          "alias": "Derek Drew",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Music ",
          "mech": "Lyricist"
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
          "callsign": "Elena",
          "alias": "Elena Petrova",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Physics And Higher Education ",
          "mech": "Physicist"
        },


        {
          "callsign": "Elizabeth",
          "alias": "Elizabeth Green",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Botany ",
          "mech": "Botanist"
        },


        {
          "callsign": "Emma",
          "alias": "Emma Rogers",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Coffee And Hospitality ",
          "mech": "Barista"
        },


        {
          "callsign": "Eric",
          "alias": "Eric Lindström",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Clandestine Services ",
          "mech": "Operations Specialist"
        },


        {
          "callsign": "Eva",
          "alias": "Eva Trinkhausen",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Data Science ",
          "mech": "Data Scientist"
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
          "callsign": "Forrest",
          "alias": "Forrest Carlisle",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Aviation ",
          "mech": "Aviationist"
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
          "callsign": "Francois",
          "alias": "Francois Felicite",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Coffee Shop ",
          "mech": "Coffee Shop Owner"
        },


        {
          "callsign": "Frans",
          "alias": "Frans van der Meer",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Wholesale ",
          "mech": "Wholesaler"
        },


        {
          "callsign": "Franz",
          "alias": "Franz Felix",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Laboratory Testing ",
          "mech": "Lab Tech"
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
          "callsign": "Gertrude",
          "alias": "Gertrude Gimmel",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Hotel & Hospitality ",
          "mech": "Guesthouse Owner"
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
          "callsign": "Gogla",
          "alias": "Gogla Khachidze",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Telemarketing ",
          "mech": "Telemarketer"
        },


        {
          "callsign": "Hans",
          "alias": "Hans Mueller",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Historical Properties ",
          "mech": "Lighthouse Manager"
        },


        {
          "callsign": "Harold",
          "alias": "Harold Hunter",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Investigation And Security Services ",
          "mech": "Investigator"
        },


        {
          "callsign": "Hassan",
          "alias": "Hassan Ahmed",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Real-Estate ",
          "mech": "Mortgage Broker"
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
          "callsign": "Isabella",
          "alias": "Isabella Santos",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Perfoming Arts ",
          "mech": "Thespian"
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
          "callsign": "Jack",
          "alias": "Jack Johnson",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "4X4 ",
          "mech": "4X4 Business Owner"
        },


        {
          "callsign": "Jackie",
          "alias": "Jackie Wong",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Video Game ",
          "mech": "Gamer"
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
          "callsign": "Jacques",
          "alias": "Jacques Bordeaux",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Wine ",
          "mech": "Wine Enthusiast"
        },


        {
          "callsign": "Jake",
          "alias": "Jake Cooper",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Supply-Chain ",
          "mech": "Courier"
        },


        {
          "callsign": "Jan",
          "alias": "Jan van der Meer",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "International Arbitration ",
          "mech": "Negotiator"
        },


        {
          "callsign": "Jane",
          "alias": "Jane Williams",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Satellite",
          "mech": "Satellite Business Owner"
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
          "callsign": "Jasmine",
          "alias": "Jasmine Montecarlo",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Health & Wellness ",
          "mech": "Beautician"
        },


        {
          "callsign": "Jason",
          "alias": "Jason Ravenwood",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Public Services ",
          "mech": "Firefighter"
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
          "callsign": "Jenni",
          "alias": "Jenni Collins",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Music ",
          "mech": "Musician"
        },


        {
          "callsign": "Jeremy",
          "alias": "Jeremy Johnson",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Risk Assessment ",
          "mech": "Actuary"
        },


        {
          "callsign": "Jerry",
          "alias": "Jerry von Himmel",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Cannabis ",
          "mech": "Grower"
        },


        {
          "callsign": "Jessi",
          "alias": "Jessi Sunderland",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Art Curation ",
          "mech": "Curator"
        },


        {
          "callsign": "Jimmy",
          "alias": "Jimmy Rodriguez",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Religious Organizations ",
          "mech": "Evangelist"
        },


        {
          "callsign": "John",
          "alias": "John Hunter",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Transportation ",
          "mech": "Captain"
        },


        {
          "callsign": "Julia",
          "alias": "Julia Juenker",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Government & Political Campaign ",
          "mech": "Politician"
        },



        {
          "callsign": "Karen",
          "alias": "Karen Chen",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "International Business ",
          "mech": "Expat"
        },


        {
          "callsign": "Kate",
          "alias": "Kate Calloway",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Brewpub ",
          "mech": "Brew Pub Owner "
        },


        {
          "callsign": "Kavango",
          "alias": "Kavango Ndhiovu",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Neurology & Mental Health Services ",
          "mech": "Neurologist"
        },


        {
          "callsign": "Lady Isabella",
          "alias": "Lady Isabella Lancaster",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Castle ",
          "mech": "Castle Owner"
        },


        {
          "callsign": "Lars",
          "alias": "Lars Johansen",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Statistical Research & Development ",
          "mech": "Statistician"
        },


        {
          "callsign": "Leila",
          "alias": "Leila Bouaziz",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "International Relations ",
          "mech": "Liaison"
        },


        {
          "callsign": "Lila",
          "alias": "Lila Kiwi",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Social Media ",
          "mech": "Influencer"
        },


        {
          "callsign": "Liv",
          "alias": "Liv Hopkins",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Beer Brewing ",
          "mech": "Brew Master"
        },


        {
          "callsign": "Liz",
          "alias": "Liz Green",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Academia And Higher Education",
          "mech": "Academic"
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
          "callsign": "Luc",
          "alias": "Luc Maretl",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Pharmaceutical ",
          "mech": "Pharmacist"
        },


        {
          "callsign": "Mara",
          "alias": "Mara Maury",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Labor Relations ",
          "mech": "Union Organizer"
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
          "callsign": "Maria",
          "alias": "Maria Gomez",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Healthcare ",
          "mech": "Registered Nurse"
        },


        {
          "callsign": "Marie",
          "alias": "Marie Dupont",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Medical ",
          "mech": "Clinician"
        },


        {
          "callsign": "Mark",
          "alias": "Mark Montana",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Real-Estate ",
          "mech": "Landowner"
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
          "callsign": "Marty",
          "alias": "Marty O’Malley",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Bartending And Hospitality ",
          "mech": "Bartender"
        },


        {
          "callsign": "Max",
          "alias": "Max Doe",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Agriculture ",
          "mech": "Agriculturist"
        },


        {
          "callsign": "Maya",
          "alias": "Maya Patel",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Cinema ",
          "mech": "Cinematographer"
        },


        {
          "callsign": "Mei Li",
          "alias": "Mei Li Li",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Export ",
          "mech": "Exporter"
        },


        {
          "callsign": "Mei-Lin",
          "alias": "Mei-Lin Chu",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Social Sciences ",
          "mech": "Sociologist"
        },


        {
          "callsign": "Melinda",
          "alias": "Melinda O’Neil",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Publishing ",
          "mech": "Writer"
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
          "callsign": "Michel",
          "alias": "Michel Montpellier",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Restaurant ",
          "mech": "Diner Owner"
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
          "callsign": "Milton",
          "alias": "Milton McAllister",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Video Game ",
          "mech": "Arcade Owner"
        },


        {
          "callsign": "Natascha",
          "alias": "Natascha Petrenko",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Biotechnology ",
          "mech": "Geneticist"
        },


        {
          "callsign": "Nikolai",
          "alias": "Nikolai Petrov",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Distilled Spirits ",
          "mech": "Distiller"
        },


        {
          "callsign": "Boris",
          "alias": "Boris Sukov",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Weekend Worker ",
          "mech": "Warrior"
        },


        {
          "callsign": "Olga",
          "alias": "Olga Petrovich",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Freelance ",
          "mech": "Remote Worker"
        },


        {
          "callsign": "Olivia",
          "alias": "Olivia Reynolds",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Art",
          "mech": "Art Gallery Owner"
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
          "callsign": "Paul",
          "alias": "Paul LeBlanc",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Franchising ",
          "mech": "Franchise Business Owner"
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
          "callsign": "Pippi",
          "alias": "Pippi Rivera",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Behavioral Health ",
          "mech": "Social Worker"
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
          "callsign": "Pierre",
          "alias": "Pierre Perrin",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Supply-Chain ",
          "mech": "Importer"
        },


        {
          "callsign": "Pim",
          "alias": "Pim Itthiwat",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Cryptocurrency ",
          "mech": "Token Developer"
        },


        {
          "callsign": "Raj",
          "alias": "Raj Rivera",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Chatbot",
          "mech": "Chatbot Developer"
        },


        {
          "callsign": "Rebecca",
          "alias": "Rebecca Patel",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Biosciences ",
          "mech": "Biologist"
        },


        {
          "callsign": "Rina",
          "alias": "Rina Jenkins",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Music ",
          "mech": "Musical Artist"
        },


        {
          "callsign": "Robert",
          "alias": "Robert Andriamaro",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Racing And Spectator Sports ",
          "mech": "Race Car Driver"
        },


        {
          "callsign": "Samantha",
          "alias": "Samantha Forester",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Animation ",
          "mech": "Animator"
        },


        {
          "callsign": "Samantha",
          "alias": "Samantha Smith",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Finance ",
          "mech": "CFO"
        },


        {
          "callsign": "Sarah",
          "alias": "Sarah Simpson",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Recruitment ",
          "mech": "Job Seeker"
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
          "callsign": "Sergei",
          "alias": "Sergei Krasny",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Nightlife ",
          "mech": "Disco Owner"
        },


        {
          "callsign": "Seth",
          "alias": "Seth Stiffel",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Conservation And Park Management ",
          "mech": "Park Ranger"
        },


        {
          "callsign": "Shelly",
          "alias": "Shelly Parker",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Protective Services ",
          "mech": "Police Officer"
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
          "callsign": "Steffi",
          "alias": "Steffi Silva",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Religious Organizations ",
          "mech": "Theologian"
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
          "callsign": "Thando",
          "alias": "Thando Mkhize",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Sponsorship ",
          "mech": "Sponsor"
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
          "callsign": "Torben",
          "alias": "Torben Thompson",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Car Dealer ",
          "mech": "Dealership Owner"
        },


        {
          "callsign": "Uwe",
          "alias": "Uwe Mueller",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Beer Garden ",
          "mech": "Beer Garden Owner "
        },


        {
          "callsign": "Viktor",
          "alias": "Viktor Kuznetsov",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Consulting ",
          "mech": "Consultant"
        },


        {
          "callsign": "Vytautas",
          "alias": "Vytautas Gudaitis",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Logistics ",
          "mech": "Logistics Manager"
        },


        {
          "callsign": "Yuri",
          "alias": "Yuri Petrov",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Space ",
          "mech": "Cosmonaut"
        },
        {
          "callsign": "Marika",
          "alias": "",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Data Science ",
          "mech": "Economist"
        },


        {
          "callsign": "Renate",
          "alias": "",
          "code": "98ca9616-044e-4f87-b89b-aae4eb3387ec///NDL-C-DEEP-STATION//6f572259-6946-41bf-931a-e0543709e892",
          "corpro": "Available",
          "frame": "Education ",
          "mech": "School Teacher"
        },


      ],
      "header": {
        "planet": "DOJO's WORLD (coming soon)",
        "year": "2023",
        "system": "Foundry VTT",
        "gate": "PUBLIC",
        "ring": "workdojos.com",
        "headerTitle": "WORKDOJOS",
        "headerSubtitle": "COMPENDIUM",
        "subheaderTitle": "BUILT WITH VANTA JS",
        "subheaderSubtitle": "MISSIONS & CO-PILOTS",
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
