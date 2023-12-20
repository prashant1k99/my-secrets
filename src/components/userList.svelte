<script lang="ts">
  import { onMount } from "svelte";
  import QRius from 'qrious'
	import UserCard from "./userCard.svelte"
	import UserQR from './loggeInUserInfo.svelte'
  const user = [
    {
      name: "Leslie Alexander",
      email: "leslie.alexander@example.com",
      profilePic: "https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
      isOnline: true,
      lastSeen: Date.now()
    },
    {
      name: "Tom Cook",
      email: "tom.cook@example.com",
      profilePic: "https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
      isOnline: false,
      lastSeen: Date.now()
    },
  ]


  export let userId:number
  export let qrKey:number
  export let userName:string

  const shareURL = window.location.href + '?id=' + userId + '&key=' + qrKey

  let qrImage: QRius | null = null

  let isDarkTheme = localStorage.getItem('theme') === 'dark';

  onMount(() => {
    const qr = new QRius({
      value: shareURL,
      size: 300,
      level: 'H',
    })
    qrImage = qr.toDataURL()
  })

  const showModal = () => {
    if (!navigator.share){
      const showQRModal = document.getElementById('showQR');
      if (showQRModal) {
        (showQRModal as HTMLDialogElement).showModal();
      }
    } else navigator.share({
      title: `Connect with ${userName}`,
      text: `Use this url to connect with ${userName} to have secret chats.`,
      url: shareURL,
      files: [new File([qrImage], 'qr.png', { type: 'image/png' })],
    })
  }
</script>
<div class="p-4 h-full overflow-y-auto">
  <div class="pt-2 px-4 flex flex-row justify-between items-center">
    Connection List:
    <button class="btn" on:click={showModal}>Add Account</button>
    <dialog id="showQR" class="modal modal-bottom sm:modal-middle">
      <div class="modal-box">
        <UserQR shareURL={shareURL} qrImage={qrImage} />
        <div class="modal-action">
          <form method="dialog">
            <button class="btn">Close</button>
          </form>
        </div>
      </div>
    </dialog>
  </div>
  <div class="divider"></div> 
  
  <ul role="list">
    {#each user as {name, email, profilePic, isOnline, lastSeen}}
    <li>
      <UserCard email={email} name={name} profilePic={profilePic} isOnline={isOnline} lastSeen={lastSeen} />
    </li>
    {/each}
  </ul>
</div>