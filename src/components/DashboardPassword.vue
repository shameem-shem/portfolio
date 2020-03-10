<template>
  <div class="dash-profile">
    <form>
        <v-row>
            <v-col>
                <v-text-field
                    class="mt-0"
                    v-model="name"
                    :error-messages="nameErrors"
                    label="Name"
                    required
                    @input="$v.name.$touch()"
                    @blur="$v.name.$touch()"
                ></v-text-field>
            </v-col>
        </v-row>
    </form>
  </div>
</template>

<script>
export default {
    
}
</script>