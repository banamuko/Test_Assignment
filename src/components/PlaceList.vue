<template>
  <div>
    <div>
      <h2>Place List</h2>
    </div>

    <div class="row">
      <div class="col-lg-4 col-md-12 mb-4" v-for="item in data1" :key="item.id">
        <div class="card testimonial-card">
          <br>
          <b-container>
            <b-row>
              <b-col cols="3">
                <b-avatar variant="info" :src="item.profile_image_url" class="mr-3" style="width: 70px; height: 70px;">
                </b-avatar>
              </b-col>
              <b-col cols="9">
                <div style="text-align:left;"><span>{{ item.name }}</span><br /></div>
                <b-row>
                  <b-col cols="9">
                    <div style="text-align:left;">
                      <b-icon icon="calendar3" font-scale="1"></b-icon>
                      <span>{{ item.operation_time[today].time_open }} AM - {{ item.operation_time[today].time_close }}
                        PM</span>
                    </div>
                  </b-col>
                  <b-col cols="3">
                    <div style="text-align:right;">
                      <b-icon icon="star-fill" font-scale="1"></b-icon>
                      <span>{{ item.rating }}</span>
                    </div>
                  </b-col>
                </b-row>
              </b-col>
            </b-row>
          </b-container>
          <br>
          <b-container>
            <b-row>
              <div class="col-lg-4 mb-2" v-for="image in item.images" :key="image.id">
                <b-col><img :src="image" style="width: 150px; height: 150px;"></b-col>
              </div>
            </b-row>

          </b-container>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import jsonfile from "./example_data.json"
export default {
  name: "placelist",
  data() {
    return {
      data1: jsonfile,
      today: 0
    };
  },
  methods: {
    getNow() {
      const d = new Date()
      let day = d.getDay()
      this.today = day
    }
  }
};
</script>