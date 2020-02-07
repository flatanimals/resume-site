<template>
  <layout>
    <div class="main-content">
      <h1 class="view-header print:text-center">Contact &amp; Information</h1>

      <div class="contact">
        <form :action="config.contact.endpoint" method="POST">
          <input type="text" name="_gotcha" style="display:none" />
          <div class="contact-form">
            <div class="contact-form-control">
              <label class="contact-label" for="contact_name">Name</label>
              <input
                class="contact-input"
                id="contact_name"
                type="text"
                name="name"
                placeholder="Firstan Lasticus"
                required
              />
            </div>
            <div class="contact-form-control">
              <label class="contact-label" for="contact_email">Email</label>
              <input
                class="contact-input"
                id="contact_email"
                type="email"
                name="_replyto"
                placeholder="flasticus@example.org"
                required
              />
            </div>
            <div class="contact-form-control">
              <label class="contact-label" for="contact_nature">Nature of Contact</label>

              <div class="inline-block relative w-full">
                <select class="contact-select" id="contact_nature" name="nature">
                  <option>Just stopping by to say Hi!</option>
                  <option>Employer searching for a fulltime employee</option>
                  <option>Business stakeholder looking for a freelance coder</option>
                  <option>Recruiter pitching a full time gig</option>
                  <option>Recruiter pitching a contract gig</option>
                  <option>Spammer that enjoys watching the world burn</option>
                  <option>Something else super important!!!</option>
                </select>

                <div
                  class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700"
                >
                  <svg
                    class="fill-current h-4 w-4"
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 20 20"
                  >
                    <path
                      d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"
                    />
                  </svg>
                </div>
              </div>
            </div>
            <div class="contact-form-control">
              <label class="contact-label" for="contact_subject">Subject</label>
              <input
                class="contact-input"
                id="contact_subject"
                type="text"
                name="subject"
                placeholder="Hear ye, hear ye!"
                required
              />
            </div>
            <div class="contact-form-control">
              <label class="contact-label" for="contact_message">Message</label>
              <textarea
                class="contact-textarea"
                id="contact_message"
                name="message"
                placeholder="I come bearing a message..."
                required
              ></textarea>
            </div>

            <div class="contact-form-control">
              <button class="contact-submit" type="submit">Send</button>
            </div>
          </div>
        </form>
      </div>
    </div>
  </layout>
</template>

<script>
// @ is an alias to /src
import Layout from "./Layout";
import config from "@/config";

export default {
  name: "contact",
  data () {
      return {
          config
      }
  },
  components: {
    Layout
  }
};
</script>
<style lang="postcss">
.contact {
  @apply mx-auto;
  @apply px-2;
  @apply mb-8;
  @apply bg-white;
  @apply shadow-lg;
}
.contact-form {
  @apply flex;
  @apply flex-col;
  @apply p-4;
}
.contact-form-control {
  @apply mb-4;
}
.contact-label {
  @apply block;
  @apply font-semibold;
  @apply font-thin;
  @apply mb-2;
  @apply pl-2;
  @apply text-gray-700;
}
.contact-input,
.contact-textarea {
  @apply p-2;
  @apply border;
  @apply rounded;
  @apply shadow;
  @apply w-full;
  @apply text-gray-700;
}
.contact-input {
  @apply leading-tight;
}

.contact-textarea {
  @apply h-48;
}
.contact-submit {
  @apply text-center;
  @apply w-full;
  @apply bg-orange-500;
  @apply rounded;
  @apply p-3;
  @apply text-lg;
  @apply text-orange-900;
  @apply font-semibold;
}
.contact-submit:hover {
  @apply text-white;
  @apply bg-teal-900;
}
.contact-select {
  @apply block;
  @apply appearance-none;
  @apply w-full;
  @apply bg-white;
  @apply text-gray-700;
  @apply border;
  @apply px-3;
  @apply py-2;
  @apply pr-8;
  @apply rounded;
  @apply shadow;
  @apply leading-tight;
}

</style>
