# Usage

The bot is designed to work with the following flow:

- New members who join your server can only see a "verification" channel (one that is not visible to anyone else).
  - Within that channel, you should run the `/start` command to set up your verification question, answers, and the role to assign. The bot will create a post explaining the process to new members, with a button to click to verify themselves.
- Upon clicking the button, the member will be asked to answer the question. If they answer incorrectly, they are kicked. If they answer correctly, they are given the verification role.
- If they do not verify in 30 minutes, they are kicked.

Ideally, you should configure the verification role such that members **with** that role cannot see the verification channel.
