<script>
    import { Card, CardActions, CardTitle, Input } from "svelte-materialify";
</script>

<div class="inputs">
    <Card outlined>
        <CardTitle>Upload associations</CardTitle>
        <CardActions>
            <input type="file" accept=".gff, .gff3, .gtf"/>
        </CardActions>
    </Card>
    <Card outlined>
        <CardTitle>Upload reference</CardTitle>
        <CardActions>
            <input type="file" accept=".gff, .gff3, .gtf"/>
        </CardActions>
    </Card>
</div>

<style lang="scss">
    .inputs {
        gap: 1rem;
        display: flex;
        flex-direction: column;
    }
</style>