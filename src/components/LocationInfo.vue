<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <div id="searchinputarea">
          <form @submit.prevent="getIframeSrc()">
            <input
              v-model="ip"
              class="form-control form-group searchinput"
              type="text"
              placeholder="Type ip adress"
            />
            <button id="searchbtn" class="btn btn-primary form-group">
              Search
            </button>
          </form>
        </div>
      </div>
      <div class="col-lg-4">
        <div class="infoarea">
          <span>
            {{ locations.ip }}
          </span>
        </div>
      </div>
      <div class="col-lg-4">
        <div class="infoarea">
          <span>
            {{ locations.location.region }}
          </span>
        </div>
      </div>
      <div class="col-lg-4">
        <div class="infoarea">
          <span>
            {{ locations.location.timezone }}
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "LocationInfo",
  mounted() {
    this.getIframeSrc();
  },
  data() {
    return {
      locations: {
        ip: "...",
        location: {
          region: "...",
          timezone: "...",
        },
      },
      ip: "",
      url: "",
    };
  },
  methods: {
    getIframeSrc() {
      axios
        .get(
          "https://geo.ipify.org/api/v1?apiKey=at_MrHGKuFmIXqQ7I8ylR2f7HP5qs6Pp&ipAddress=" +
            this.ip
        )
        .then((loc) => {
          this.locations = loc.data;
          this.$emit(
            "mapurl",
            "https://maps.google.com/maps?q=" +
              loc.data.location.lat +
              "," +
              loc.data.location.lng +
              "&hl=az&z=14&output=embed"
          );
        });
    },
  },
};
</script>

<style  scoped>
.infoarea {
  background-color: gainsboro;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100px;
  padding-top: 20px;
  padding-bottom: 20px;
}
#searchinputarea {
  padding-top: 20px;
  padding-bottom: 20px;
}
#searchbtn {
  width: 100%;
  background: #36393dd2;
}
</style>