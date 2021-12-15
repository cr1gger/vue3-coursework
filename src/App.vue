<template>
  <div className="container column">
    <app-constructor @addBlockEvent="addBlock"></app-constructor>
    <div className="card card-w70">
      <h3 v-if="!visibleBlocks">Добавьте первый блок, чтобы увидеть результат</h3>
      <div v-else>
          <div v-for="block in resumeBlock">
              <resume-header v-if="block.type === TYPE_HEADER" :value="block.value"></resume-header>
              <resume-avatar v-if="block.type === TYPE_AVATAR" :value="block.value"></resume-avatar>
              <resume-sub-header v-if="block.type === TYPE_SUBHEADER" :value="block.value"></resume-sub-header>
              <resume-desc v-if="block.type === TYPE_TEXT" :value="block.value"></resume-desc>
          </div>
      </div>
    </div>
  </div>
  <resume-comments/>

</template>

<script>
import AppConstructor from "./components/AppConstructor";
import ResumeAvatar from "./components/ResumeAvatar";
import ResumeDesc from "./components/ResumeDesc";
import ResumeHeader from "./components/ResumeHeader";
import ResumeSubHeader from "./components/ResumeSubHeader";
import ResumeComments from "./components/ResumeComments";


export default {
  data() {
    return {
      TYPE_HEADER: 'title',
      TYPE_SUBHEADER: 'subtitle',
      TYPE_AVATAR :'avatar',
      TYPE_TEXT: 'text',

      resumeBlock: []
    }
  },
  methods: {
    addBlock(data) {
      this.resumeBlock.push({
        value: data.value,
        type: data.type
      })
    }
  },
  computed: {
    visibleBlocks() {
      return this.resumeBlock.length > 0
    }
  },
  components: {
    AppConstructor,
    ResumeAvatar,
    ResumeDesc,
    ResumeHeader,
    ResumeSubHeader,
    ResumeComments
  }
}
</script>
