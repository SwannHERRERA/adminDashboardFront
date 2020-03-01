<template>
  <div class="container mx-auto mt-5">
    <form>
      <form-group design="underline" placeholder="Loup"
        >Nom de la conversation</form-group
      >
      <div v-for="(admin, i) in admins" :key="admin._id">
        <form-group design="underline" placeholder="Loup"
          >Administrateur N°{{ i + 1 }}</form-group
        >
      </div>
    </form>
  </div>
</template>
<script>
import formGroup from '@/components/molecules/formGroup.vue'
export default {
  components: {
    'form-group': formGroup
  },
  data: () => {
    return {
      admins: [
        {
          _id: { $oid: '5e4da7401c9f7a3350edba89' },
          email: 'h.houis@gmail.com',
          password:
            '$2b$08$3JRKnMI4keq5ITY/.Iy/Tes0Dh/tYRLXbqJWNttfZyNGtQrVhZ3jK',
          name: 'Hugo Houis',
          tokens: [
            {
              _id: { $oid: '5e4da7401c9f7a3350edba8a' },
              token:
                'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI1ZTRkYTc0MDFjOWY3YTMzNTBlZGJhODkiLCJpYXQiOjE1ODIxNDczOTJ9.DTc9GeAMYuh98dvoY96Yq_KPS9OHX_SVtTk4vQD58ug'
            }
          ],
          __v: { $numberInt: '1' }
        }
      ]
    }
  }
}
</script>
