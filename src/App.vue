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
          "slug": "002",
          "name": "Academic Workplace Revolution",
          "status": "start"
        },
        {
          "slug": "004",
          "name": "AI Bias and Ethical Concerns",
          "status": "start"
        },
        {
          "slug": "005",
          "name": "Art Industry Revolution",
          "status": "start"
        },
        {
          "slug": "006",
          "name": "Automated Quality Control for the Manufacturing Industry",
          "status": "start"
        },
        {
          "slug": "007",
          "name": "Bartender Automation and Efficiency",
          "status": "start"
        },
        {
          "slug": "008",
          "name": "Beauty-Wellness Connection",
          "status": "start"
        },
        {
          "slug": "009",
          "name": "Beer Garden Optimization Challenge",
          "status": "start"
        },
        {
          "slug": "010",
          "name": "Boosting Customer Engagement through Interactive Content Marketing",
          "status": "start"
        },
        {
          "slug": "011",
          "name": "Boosting Customer Engagement through Interactive Content Marketing",
          "status": "start"
        },
        {
          "slug": "Boosting Sales & Marketing Productivity",
          "name": "Boosting Sales & Marketing Productivity",
          "status": "start"
        },
        {
          "slug": "012",
          "name": "Brief: Remote Barista Initiative",
          "status": "start"
        },
        {
          "slug": "013",
          "name": "Castle Industry Crisis Management Team",
          "status": "start"
        },
        {
          "slug": "014",
          "name": "Community Services Volunteer Initiative",
          "status": "start"
        },
        {
          "slug": "015",
          "name": "Consequences for the Aviation Industry",
          "status": "start"
        },
        {
          "slug": "Content Creation for Social Media",
          "name": "Content Creation for Social Media",
          "status": "start"
        },
        {
          "slug": "016",
          "name": "Develop a new energy storage solution for renewable energy sources",
          "status": "start"
        },
        {
          "slug": "017",
          "name": "Develop Plant-based Fertilizer",
          "status": "start"
        },
        {
          "slug": "018",
          "name": "Digital Preservation in the Real World",
          "status": "start"
        },
        {
          "slug": "019",
          "name": "Disco Ownership Solutions Team",
          "status": "start"
        },
        {
          "slug": "020",
          "name": "Distilled Spirits Industry Challenge",
          "status": "start"
        },
        {
          "slug": "021",
          "name": "Electronic Ticketing System for Musicians",
          "status": "start"
        },
        {
          "slug": "022",
          "name": "Exporters Assistance Program",
          "status": "start"
        },
        {
          "slug": "023",
          "name": "Fiduciary & Security Services Industry",
          "status": "start"
        },
        {
          "slug": "024",
          "name": "Financial Risk Management",
          "status": "start"
        },
        {
          "slug": "025",
          "name": "Financial Services Industry Challenge",
          "status": "start"
        },
        {
          "slug": "026",
          "name": "Firefighters Remote Solution",
          "status": "start"
        },
        {
          "slug": "147",
          "name": "Gaming Solutions",
          "status": "start"
        },
        {
          "slug": "027",
          "name": "The Effect of Artificial Intelligence on Employment",
          "status": "start"
        },
        {
          "slug": "028",
          "name": "Impact of Programmatic Advertising on Consumer Trust",
          "status": "start"
        },
        {
          "slug": "029",
          "name": "Improving Access to Behavioral Health Services for Low-Income Populations",
          "status": "start"
        },
        {
          "slug": "030",
          "name": "Improving Access to Healthcare for Rural Communities",
          "status": "start"
        },
        {
          "slug": "032",
          "name": "Improving Brew Pub Operations During the COVID-19 Pandemic",
          "status": "start"
        },
        {
          "slug": "033",
          "name": "Improving Communication and Collaboration in Remote Teams",
          "status": "start"
        },
        {
          "slug": "031",
          "name": "Improving Advisor Productivity",
          "status": "start"
        },
        {
          "slug": "034",
          "name": "Improving Consultant Productivity",
          "status": "start"
        },
        {
          "slug": "035",
          "name": "Improving Crop Yields for the Cannabis Industry",
          "status": "start"
        },
        {
          "slug": "036",
          "name": "Improving Crop Yields in Drought-Prone Areas",
          "status": "start"
        },
        {
          "slug": "037",
          "name": "Improving Customer Experience in Cafes",
          "status": "start"
        },
        {
          "slug": "038",
          "name": "Improving Customer Experience in the Guesthouse Industry",
          "status": "start"
        },
        {
          "slug": "039",
          "name": "Improving Customer Retention in the Franchising Industry",
          "status": "start"
        },
        {
          "slug": "040",
          "name": "Improving Customer Satisfaction in Telemarketing",
          "status": "start"
        },
        {
          "slug": "041",
          "name": "Improving Customer Satisfaction in the Travel Industry",
          "status": "start"
        },
        {
          "slug": "042",
          "name": "Improving Diplomatic Relations with North Korea",
          "status": "start"
        },
        {
          "slug": "043",
          "name": "Improving Efficiency in Freight Transportation",
          "status": "start"
        },
        {
          "slug": "044",
          "name": "Improving Freelance Payments for Digital Nomads",
          "status": "start"
        },
        {
          "slug": "045",
          "name": "Improving Labor Relations for Union Organizers",
          "status": "start"
        },
        {
          "slug": "046",
          "name": "Improving Medication Adherence for Chronic Conditions",
          "status": "start"
        },
        {
          "slug": "047",
          "name": "Improving Medication Administration Accuracy in the Healthcare Industry",
          "status": "start"
        },
        {
          "slug": "048",
          "name": "Improving Music Industry Monetization for Lyricists",
          "status": "start"
        },
        {
          "slug": "049",
          "name": "Improving Pain Management for Chronic Pain Patients",
          "status": "start"
        },
        {
          "slug": "050",
          "name": "Improving Patient Outcomes with Telemedicine",
          "status": "start"
        },
        {
          "slug": "051",
          "name": "Improving Prescription Accuracy for the Pharmaceutical Industry",
          "status": "start"
        },
        {
          "slug": "052",
          "name": "Improving Remote Work Efficiency for App Developers",
          "status": "start"
        },
        {
          "slug": "053",
          "name": "Improving Reputation Management for the Public Relations Industry",
          "status": "start"
        },
        {
          "slug": "054",
          "name": "Improving Restaurant Operations in the New Normal",
          "status": "start"
        },
        {
          "slug": "055",
          "name": "Improving Self-Governance for Teams",
          "status": "start"
        },
        {
          "slug": "056",
          "name": "Improving Small Business Sales through E-Commerce Solutions",
          "status": "start"
        },
        {
          "slug": "057",
          "name": "Improving Supply Chain Efficiency with Technology",
          "status": "start"
        },
        {
          "slug": "059",
          "name": "Improving Supply-Chain Efficiency",
          "status": "start"
        },
        {
          "slug": "Improving Supply-Chain Efficiency in the Importation Industry",
          "name": "Improving Supply-Chain Efficiency in the Importation Industry",
          "status": "start"
        },
        {
          "slug": "060",
          "name": "Improving Sustainable Outdoor Exploration",
          "status": "start"
        },
        {
          "slug": "061",
          "name": "Improving the Accuracy of Predictive Analytics",
          "status": "start"
        },
        {
          "slug": "062",
          "name": "Improving the Efficiency of Political Decision Making Processes",
          "status": "start"
        },
        {
          "slug": "063",
          "name": "Improving the Efficiency of Remote Consulting Teams",
          "status": "start"
        },
        {
          "slug": "064",
          "name": "Improving the Impact of Spiritual Coaching in the Workplace",
          "status": "start"
        },
        {
          "slug": "065",
          "name": "International Arbitration Industry Reform",
          "status": "start"
        },
        {
          "slug": "066",
          "name": "Lab Testing Industry Optimization",
          "status": "start"
        },
        {
          "slug": "067",
          "name": "Legal Industry Transformation Challenge",
          "status": "start"
        },
        {
          "slug": "068",
          "name": "Lending Industry Reimagined",
          "status": "start"
        },
        {
          "slug": "069",
          "name": "Live Event Industry Recovery Plan",
          "status": "start"
        },
        {
          "slug": "070",
          "name": "Marketing Services Industry Lead Generation Project",
          "status": "start"
        },
        {
          "slug": "071",
          "name": "Marketing Strategy for Small Town Tourism",
          "status": "start"
        },
        {
          "slug": "072",
          "name": "Motivational Speaking Industry Revolution",
          "status": "start"
        },
        {
          "slug": "073",
          "name": "Non-Profit Collaboration to Solve Fundraising Challenges",
          "status": "start"
        },
        {
          "slug": "074",
          "name": "Operations Specialist Remote Challenge",
          "status": "start"
        },
        {
          "slug": "075",
          "name": "Optimizing Delivery Routes for the Logistics Industry",
          "status": "start"
        },
        {
          "slug": "076",
          "name": "Optimizing Machining Processes for Energy Efficiency",
          "status": "start"
        },
        {
          "slug": "077",
          "name": "Predictive Maintenance for Smart Factories",
          "status": "start"
        },
        {
          "slug": "078",
          "name": "Preservation of Historical Properties",
          "status": "start"
        },
        {
          "slug": "079",
          "name": "Protecting and Revitalizing our National Park System",
          "status": "start"
        },
        {
          "slug": "080",
          "name": "Real-Estate Industry Services",
          "status": "start"
        },
        {
          "slug": "081",
          "name": "Real-Estate Industry Solutions",
          "status": "start"
        },
        {
          "slug": "082",
          "name": "Real-world Consequences for the Cryptocurrency Industry",
          "status": "start"
        },
        {
          "slug": "083",
          "name": "Recruitment Industry Revolution",
          "status": "start"
        },
        {
          "slug": "084",
          "name": "Recruitment Industry Solutions for Job Seekers",
          "status": "start"
        },
        {
          "slug": "085",
          "name": "Reinventing the Record Label Industry",
          "status": "start"
        },
        {
          "slug": "086",
          "name": "Remote Botanical Project",
          "status": "start"
        },
        {
          "slug": "087",
          "name": "Remote Evangelism Solutions",
          "status": "start"
        },
        {
          "slug": "088",
          "name": "Remote International Business Solutions",
          "status": "start"
        },
        {
          "slug": "089",
          "name": "Remote Life Coaching for the Life Coaching Industry",
          "status": "start"
        },
        {
          "slug": "090",
          "name": "Remote R&D Solutions for the R&D Industry",
          "status": "start"
        },
        {
          "slug": "091",
          "name": "Remote Real Estate Solutions for Mortgage Brokers",
          "status": "start"
        },
        {
          "slug": "092",
          "name": "Remote Sales Coaching Initiative",
          "status": "start"
        },
        {
          "slug": "093",
          "name": "Remote Space Debris Mitigation and Removal",
          "status": "start"
        },
        {
          "slug": "094",
          "name": "Remote Study of Mental Health",
          "status": "start"
        },
        {
          "slug": "095",
          "name": "Renewable Energy Sources",
          "status": "start"
        },
        {
          "slug": "096",
          "name": "Revamp of the Sales & Marketing Industry with Social Media Management",
          "status": "start"
        },
        {
          "slug": "097",
          "name": "Revamping the Virtual Classroom Experience",
          "status": "start"
        },
        {
          "slug": "003",
          "name": "A Remote Photojournalism Project",
          "status": "start"
        },
        {
          "slug": "098",
          "name": "Revitalizing the Arcade Industry",
          "status": "start"
        },
        {
          "slug": "099",
          "name": "Revitalizing the Art Industry",
          "status": "start"
        },
        {
          "slug": "100",
          "name": "Revitalizing the Beer Brewing Industry",
          "status": "start"
        },
        {
          "slug": "101",
          "name": "Revitalizing the Performing Arts Industry",
          "status": "start"
        },
        {
          "slug": "102",
          "name": "Revitalizing the Publishing Industry for Ghostwriters",
          "status": "start"
        },
        {
          "slug": "103",
          "name": "Revolutionize the Automotive Industry for Dealership Owners",
          "status": "start"
        },
        {
          "slug": "104",
          "name": "Revolutionizing Book-keeping for Administrators",
          "status": "start"
        },
        {
          "slug": "105",
          "name": "Revolutionizing Higher Education Industry",
          "status": "start"
        },
        {
          "slug": "106",
          "name": "Revolutionizing Journalism",
          "status": "start"
        },
        {
          "slug": "107",
          "name": "Revolutionizing the Advertising Industry",
          "status": "start"
        },
        {
          "slug": "108",
          "name": "Revolutionizing the Exhibition Industry",
          "status": "start"
        },
        {
          "slug": "Revolutionizing the Film Industry",
          "name": "Revolutionizing the Film Industry",
          "status": "start"
        },
        {
          "slug": "Revolutionizing the Film Industry for Screenwriters",
          "name": "Revolutionizing the Film Industry for Screenwriters",
          "status": "start"
        },
        {
          "slug": "111",
          "name": "Revolutionizing the Martial Arts Industry",
          "status": "start"
        },
        {
          "slug": "110",
          "name": "Revolutionizing the Publishing Industry",
          "status": "start"
        },
        {
          "slug": "112",
          "name": "Revolutionizing the Startup Financing Industry",
          "status": "start"
        },
        {
          "slug": "113",
          "name": "Revolutionizing the Travel Industry for Backpackers",
          "status": "start"
        },
        {
          "slug": "114",
          "name": "Revolutionizing the Workplace for Philosophers",
          "status": "start"
        },
        {
          "slug": "115",
          "name": "Revolutionizing the Workplace for Web Designers",
          "status": "start"
        },
        {
          "slug": "116",
          "name": "Revolutionizing the Writing & Publishing Industry",
          "status": "start"
        },
        {
          "slug": "117",
          "name": "Revolutionizing Web Design",
          "status": "start"
        },
        {
          "slug": "118",
          "name": "Risk Assessment Model for Natural Disasters",
          "status": "start"
        },
        {
          "slug": "119",
          "name": "Social Media Influencer Campaign for Better Online Privacy",
          "status": "start"
        },
        {
          "slug": "120",
          "name": "Sociological Solutions for Social Inequality",
          "status": "start"
        },
        {
          "slug": "121",
          "name": "Solve Police Corruption in 90 Days",
          "status": "start"
        },
        {
          "slug": "122",
          "name": "Solve the Publishing Industry Puzzle",
          "status": "start"
        },
        {
          "slug": "123",
          "name": "Streamlining the Freelance Industry",
          "status": "start"
        },
        {
          "slug": "124",
          "name": "Sustainability in the Coffee Industry",
          "status": "start"
        },
        {
          "slug": "125",
          "name": "The Biotech Revolution",
          "status": "start"
        },
        {
          "slug": "126",
          "name": "The Climate Change Crisis for Yogis",
          "status": "start"
        },
        {
          "slug": "127",
          "name": "The Digital Marketing Crisis",
          "status": "start"
        },
        {
          "slug": "128",
          "name": "The Effect of Artificial Intelligence on Employment",
          "status": "start"
        },
        {
          "slug": "129",
          "name": "The Future of Cinema",
          "status": "start"
        },
        {
          "slug": "130",
          "name": "The Future of Racing",
          "status": "start"
        },
        {
          "slug": "131",
          "name": "The Future of Religious Organizations",
          "status": "start"
        },
        {
          "slug": "132",
          "name": "The Future of Sustainable Design",
          "status": "start"
        },
        {
          "slug": "133",
          "name": "The Impact of Climate Change on the Outdoor Adventure Industry",
          "status": "start"
        },
        {
          "slug": "134",
          "name": "The Remote Revolution in Performing Arts",
          "status": "start"
        },
        {
          "slug": "135",
          "name": "The Remote Startup Industry Challenge",
          "status": "start"
        },
        {
          "slug": "136",
          "name": "The Retail Industry Challenge",
          "status": "start"
        },
        {
          "slug": "138",
          "name": "The Weekend Warrior Challenge",
          "status": "start"
        },
        {
          "slug": "139",
          "name": "The Wholesale Industry Puzzle",
          "status": "start"
        },
        {
          "slug": "140",
          "name": "Uncovering Corporate Espionage",
          "status": "start"
        },
        {
          "slug": "141",
          "name": "Virology Study",
          "status": "start"
        },
        {
          "slug": "142",
          "name": "Virtual Managed Services Project",
          "status": "start"
        },
        {
          "slug": "143",
          "name": "Virtual Physical Therapy Platform",
          "status": "start"
        },
        {
          "slug": "144",
          "name": "Virtual Reality Training and Safety Standards",
          "status": "start"
        },
        {
          "slug": "145",
          "name": "Wine Industry Puzzle Challenge",
          "status": "start"
        },
        {
          "slug": "146",
          "name": "Zookeeper Puzzle",
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
          "callsign": "Susanna",
          "alias": "Samantha Forester",
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
          "alias": "Renate",
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
