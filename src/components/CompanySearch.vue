<template>
  <v-container>
    <v-row justify="center">
      <v-col cols="6">
       <v-sheet
          color="white"
          elevation="1"
          height="80vh"
          width="100%"
        >
          <v-row class="ma-1">
            <div class="text-h6">企業を追加</div>
          </v-row>

          <v-row class="ma-1">
            <v-text-field @change="handleKeywordChange" @click:append-outer="search" append-outer-icon="mdi-magnify"></v-text-field>
          </v-row>

          <v-row class="ma-1">
            <div class="body-2">検索結果</div>
          </v-row>

          <v-row class="ma-1">
            <v-list dense width="100%">
              <v-list-item-group >
                <v-list-item
                  v-for="(company, i) in searchResult"
                  :key="i"
                >
                  <v-list-item-content @click="addCompany(company.id)">
                    <v-list-item-title v-text="company.name"></v-list-item-title>
                  </v-list-item-content>
                  <v-list-item-icon>
                    <v-icon >mdi-plus</v-icon>
                  </v-list-item-icon>
                </v-list-item>
              </v-list-item-group>
            </v-list>

          </v-row>

        </v-sheet>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'CompanySearch',
  props: {
    searchResult: {
      type: Array,
      default: function () {
        return ([
          {
            id: 1,
            name: 'sony'
          },
          {
            id: 2,
            name: 'hitatch'
          },
          {
            id: 3,
            name: 'pana'
          }
        ])
      }
    },
    // チャートに表示するためにすでに選択されている企業のリスト
    companiesForChart: {
      type: Array,
      default: function () {
        return ([{
          id: 3,
          name: 'pana'
        }])
      }
    }
  },
  data: () => ({
    additionalCompanies: [],
    searchKeyword: ''
  }),
  methods: {
    handleKeywordChange: function (value) {
      this.searchKeyword = value
    },
    search: function (event) {
      console.log(`Search: ${this.searchKeyword}`)
    },
    addCompany: function (companyId) {
      this.additionalCompanies.push(companyId)
      console.log(this.additionalCompanies)
    }
  }
}
</script>
