# Duplicity for Solodev
This repository is used to backup, export backups, and restore backups on Solodev instances using Duplicity. Backups are stored in designated <a href="https://aws.amazon.com/s3/">Amazon S3</a> buckets. Using Duplicity, backups can be run on a schedule or on demand and produce encryped snapshots in a specified S3 bucket. Using the custom export process, backups can then be copied to any designated mount. Similarly, using the restore process, a specified backup can overwrite a production environment.

## What is Duplicity?
<a href="http://duplicity.nongnu.org/">Duplicity</a> is a backup utility that is both efficient and encrypted. Backups are generated on an incremental basis so that only the parts of files that have changed will be archived, thus ensuring efficiencies in space/size management. Each archive is also encrypted with signatures to ensure only authorized users and utilities have access.

## Environment Variables
<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>BUCKET</td>
    <td>The name of the S3 bucket and any corresponding directory path to the folder that stores the backup files.</td>
  </tr>
  <tr>
    <td>GPG_PW</td>
    <td>The <a href="http://www.gnupg.org/">GnuPG</a> password to encrypt backups and decrypt archives during a restore or export event.</td>
  </tr>
  <tr>
    <td>IAM_ACCESS_KEY</td>
    <td>The IAM Access key ID that corresponds to the IAM user with sufficient policy access to the designated S3 backup bucket.</td>
  </tr>
  <tr>
    <td>IAM_SECRET_KEY</td>
    <td>The IAM Secret key that corresponds to the IAM user with sufficient policy access to the designated S3 backup bucket.</td>
  </tr>
  <tr>
    <td>MOUNT</td>
    <td>The directory path of what to backup in a backup event or where to restore in a restore event.</td>
  </tr>
  <tr>
    <td>PROCESS</td>
    <td>The type of process to run such as "restore", or "export". If none is specified, defaults to a backup event.</td>
  </tr>
  <tr>
    <td>TIME</td>
    <td>A <a href="http://duplicity.nongnu.org/vers7/duplicity.1.html#sect8">Duplicity-compatible</a> time format to retrive specific point-in-time backups.</td>
  </tr>
  <tr>
    <td>BACKUP_LOCATION</td>
    <td>A designated location (such as a local directory) to store files during an export event.</td>
  </tr>              
</table>

## Usage
<strong>Export<strong><br>
To export a specific backup, please use these instructions:
<ol>
  <li>Clone the repo to your local or virtual machine</li>
  <li>CD into the directory root</li>
  <li>Add a .env Environment file with the above variables defined</li>
  <li>Run `docker-compose up`</li>
</ol>