<template>
  <div class="recruit layout-width">
    <el-row :gutter="45">
      <el-col v-for="(item, index) in RecruitList" :key="index" class="project-item" :span="8">
        <project-item :detail="item" :pagename="pageName" />
      </el-col>
    </el-row>
    <el-card v-if="RecruitList.length>=9" shadow="always" class="show-more" :body-style="{padding:'5px'}">
      <div v-show="!loading" class="more" @click="handelmore">
        加载更多<i class="el-icon-arrow-right" /><i class="el-icon-arrow-right" />
      </div>
      <el-table
        v-show="loading"
        v-loading="loading"
        style="width: 100%;height:40px"
      />
    </el-card>
  </div>
</template>

<script>
import { getRecruitList } from '@/api'
import ProjectItem from '@/components/Recruit/ProjectItem'
export default {
  name: 'Recruit',
  components: {
    ProjectItem
  },
  data() {
    return {
      RecruitList: [],
      pageName: 'recruit',
      page: 1,
      size: 9,
      loading: false
    }
  },
  mounted() {
    this.getData()
  },
  methods: {
    getData() {
      getRecruitList({ page: this.page, size: this.size }).then((res) => {
        const data = res.data
        if (this.page > 1) {
          data.forEach(val => {
            this.RecruitList.push(val)
          })
        } else {
          this.RecruitList = data
        }
      })
    },
    handelmore() {
      this.page++
      this.getData()
      this.loading = true
      this.getData()
      setTimeout(() => {
        this.loading = false
      }, 1000)
    }
  }
}
</script>

<style lang="scss" scoped>
  .recruit {
    padding-top: 50px;
    .project-item {
      position: relative;
      top: 0px;
      transition: all 0.3s linear;
      &:hover{
        top:-10px;
      }

    }
    .show-more{
      margin-bottom: 50px;
      display: flex;
      justify-content: center;
      // height: 40px;
      .more{
        cursor: pointer;
        font-size:16px;
        font-weight:400;
        color:rgba(54,174,173,1);
        line-height:40px;
        i{
          display: inline-block;
          width: 10px;
        }
      }
    }
  }

</style>
