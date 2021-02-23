<template>
  <v-row>
			<v-col>
				<experience-detail
					:posts="content.metadata.academic"
					title="Education"
				/>
      </v-col>
      <v-col>
				<experience-detail
					:posts="content.metadata.professional"
					title="Professional"
				/>
			</v-col>
  </v-row>
</template>

<script>
import ExperienceDetail from "./ExperienceDetail.vue"

export default {
  name: "Experience",
  props: ["content"],
  components: {
    ExperienceDetail
  }
}
</script>

<style>

</style>